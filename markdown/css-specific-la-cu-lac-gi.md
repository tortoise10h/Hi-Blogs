Chúng ta sẽ đi tới một ví dụ để có thể dễ dàng hình dung hơn. Giả sử chúng ta có đoạn code sau đây:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/y8h2jw8nyi_image.png)
Ở đoạn code trên, phần xét `background-color` cho element `h1` đã cùng lúc bị xét 2 lần ở cả `h1` với `background-color` là màu cam và class `content` với `background-color` là xanh và cùng xem chuyện gì xảy ra tiếp theo
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/sycq1mugu2_image.png)
Xin lỗi nhưng <i class='em em-laughing'></i>
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/5yse1eujwd_image.png)
 Vậy những gì đã xảy ra ở trên đã cho ta thấy **Specificity** là như thế nào. Nếu có 2 hoặc nhiều hơn "CSS rules" (mình chưa biết gọi trong tiếng việt sao cho ngầu cả <i class='em em-laughing'></i>)  cùng nhắm vào một thằng element thì khi đó trình duyệt sẽ tuần theo một nguyên tắc và xem trong đống CSS rules kia thằng nào xứng đáng nhất để chọn ra và apply vào element, đó là cách giải thích **specificity** đơn giản mà mình biết. Ban đầu mình cũng đã lầm tưởng là nó sẽ chuyển sang màu cam vì mình vẫn nghĩ thằng `h1` gần với `body` hơn nên CSS của nó sẽ được apply, nhưng lại **hoàn toàn không phải** (đôi khi mình gần cô gái mình yêu hơn thằng khác nhưng nó giàu hơn nên thế là <i class='em em-sob'></i>). Để dễ dàng hơn chúng ta hãy tưởng tượng **specificity** như là một bảng xếp hạng mà trong đống CSS rules thằng nào hạng cao hơn thì nó được apply vào element (như kiểu chọn rể cho mị nương ấy :v).
## Bảng xếp hạng Specificity 
Để giải thích trường hợp ở trên *"đôi khi mình gần cô gái mình yêu hơn thằng khác nhưng nó giàu hơn nên thế là <i class='em em-sob'></i>"*, thực ra là cái này *" Nếu có 2 hoặc nhiều hơn CSS rules cùng nhắm vào một thằng element thì khi đó trình duyệt sẽ tuần theo một nguyên tắc và xem trong đống CSS rules kia thằng nào xứng đáng nhất để chọn ra và apply vào element"*. Ở đây chúng ta sẽ có bảng xếp hạng cho CSS rule để trình duyệt tuân theo khi apply CSS, theo thứ tự từ trên xuống dưới.
* **inline-style**: Đây là lúc mà chúng ta style cho element mà ta muốn vào thằng dòng đó như thế này
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/b0wss1m05a_image.png)  thì nó sẽ apply vào element đó theo những gì mà chúng ta đã style trên dòng đó và mặc kệ nó bên file CSS hay trên phần `style` ở `head` chúng ta đã quy định cho nó như thế nào. Nó có thể xem là **Đệ nhất** (bỏ qua trường hợp của `!important` chúng ta sẽ nói sau)
* **ID**: tiếp sau **Đệ nhất** thì sẽ là **Đệ nhị** ID, nếu không có **inline-style** thì khi cả class, style cho element, vân vân mây mây đều trỏ chung vào element mà ID đó đang trỏ thì đều bại dưới tay ID hết.
* **Class,  attributes và pseudo-classes**: Tiếp theo ID ở trên chúng ta sẽ có nhóm **Đệ tam** bao gồm: class, thuộc tính ([attribute nào đó]) và các pseudo-classes như `:hover`, `:focus`, etc
* **Elemen và pseudo-elements**: Cuối cùng là nhóm em út gồm: các element như `h1` `li`,.. và các pseudo-elements như `::before`, `::after`, etc

Và đó là bảng thứ tự mà trình duyệt dựa vào khi gặp nhiều CSS rules trỏ vào một element hoặc ta có thể xem hình sau để dễ mường tượng hơn
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/pw01w8t5hy_image.png)
(hình \*)
(*ảnh này là của CSS tricks mình sẽ để link ở cuối bài*)
## Tính toán giá trị của CSS specificity
Tính toán giá trị của CSS specificity để biết được cái nào là được apply vào element để chúng ta không bị mắc lỗi khi viết CSS xong lại hét lên *"Bố kêu mày màu xanh sao mày lại ra màu đỏ"* chỉ vì lí do chúng ta viết thằng màu xanh có giá trị Specificity thấp hơn thằng màu đỏ. 
Ta có đoạn code sau:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/3jx3tlud39_image.png)
Dựa vào bảng thứ tự ở trên (hình \*) giá trị **specicficity** được tính như sau:
* **Inline-style**: ở đây ta có một **inline-style** đó là `background-color:#1abc9c` cho nên điểm của nó sẽ là 1,0,0,0 (hay 1000) 
* **ID**: chúng ta có 1 ID `content` tuy nhiên nó có thêm một element `h1` phía sau cho nên điểm của nó sẽ là 0,1,0,1 (hay 101)
* **Element**: Ta có một element `h1` tương ứng với điểm 0,0,0,1 (hay 1) không tính `h1` ở trên bởi vì nó thuộc về ID `content`

Vậy, theo như ta thấy 1 < 101 < 1000 cho nên rõ ràng là CSS `background-color:#1abc9c` của **inline-style** sẽ được áp dụng (quá đơn giản đúng không nào <i class='em em-laughing'></i>)

## Một số đạo luật trong CSS
### Equal specificity: the latest rule counts
Equal specificity: the latest rule counts (hay thuần việt tí là "Nếu hai thằng có giá trị specificity bằng nhau, thằng nào viết sau thằng đó được apply")
Trường hợp ta có hai CSS rules có hạng ngang nhau như thế này:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/ib6tftqol6_image.png) rõ ràng là giá trị specificity của nó là như nhau (đều là element `h1`) lúc này chúng ta sẽ theo luật *"thằng nào gần hơn thằng đó thắng"*. Cho nên kết quả hiển nhiên là
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/hvzq2hb1lm_image.png)
Nếu đảo ngược lại
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/m8fwh0p00u_image.png)
Thì sẽ được như này:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/bog84cujph_image.png)
### ID selectors have a higher specificity than attribute selectors
ID selectors have a higher specificity than attribute selectors: ID selector thì sẽ có giá trị specificity cao hơn so với attribute selector. Ví dụ:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/isyodl9nn8_image.png) Và như đã nói, ID selector là kẻ dành chiến thắng
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/d24if98gtp_image.png)
### As specific as it makes sense to be
 As specific as it makes sense to be: Càng cụ thể càng tốt. Để dễ dàng hiểu rõ ta nhìn ví dụ dưới đây:
 ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/s5s0u27ygx_image.png)
 Bạn có 1 đống code như trên với mục đích là in ra mấy cái link và xét `background-color` cho nó là đỏ.
 ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/satt8swhte_image.png)
 Tuy nhiên link 1 là link bạn yêu thích vì nó chứa *"tư liệu học tập"* nên bạn sẽ cho nó qua một màu khác để dễ nhận biết. Bạn lập tức vào chỉnh sửa một tí với suy nghĩ trong đầu là nó sẽ sang màu khác để lần sau tìm link *"học tập"* dễ dàng hơn.
 ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/eux2mwhtxe_image.png)
 tuy nhiên, nó vẫn là 3 link đỏ lòe không thay đổi, bởi vì rõ ràng là tính ra thằng ID là **đệ nhị** quyền lực nó vẫn cao hơn thằng class bạn cử ra chỉ là **đệ tam**. Cho nên ta mới nói *"càng cụ thể càng tốt"*, nếu chúng ta sửa lại như thế này
 ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/xa55r62jg_image.png)
 Thì kết quả sẽ trở nên viên mãn hơn, bởi vì nó cụ thể hơn việc chỉ ghi mỗi thằng class `special` và quăng vào trong cái `li` kia.
 ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/6o6d9bijl7_image.png)
## !Important
Như đã nói lúc phân cấp cho **Inline-style** thì trên nó vẫn có thằng có quyền lực cao hơn đó là **!important** (cao nhân ắt có cao nhân trị). Nếu bạn chỉ dùng một con tốt thí element có giá trị là Specificity là 1 và trên đó là một đống class, ID, etc cùng với **inline-style**
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/rzp9ez4kvw_image.png)
Thì phần thắng rõ ràng thuộc về **inline-style** dựa theo vị trí bảng xếp hạng
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/e4ntg4badc_image.png)
Nhưng khi đặt **!important** vào thì con tốt thí đó cũng sẽ hóa chaos
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/uxclepdvf0_image.png)
Kết quả:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/ujqbqybh51_image.png)
Nhìn qua thì thấy **!important** quá là quyền năng đúng không nào, tuy nhiên cũng vì lí do đó nên là nó rất dễ bị lạm dụng nếu không hiểu rõ về nó. Vậy nên chúng ta cần tìm hiểu rõ về **!important** để không bị rơi vào tình trạng lạm dụng nó và giúp code CSS chúng ta sạch sẽ hơn.
##Link bài tham khảo
Mình tham khảo tại:
* W3School [ở đây](https://www.w3schools.com/css/css_specificity.asp)
* CSS-tricks [ở đây](https://css-tricks.com/specifics-on-css-specificity/)


<<<<<Blog-Meta-Data>>>>>
title:CSS specific là củ lạc gì?;publishMode:publish;tags:TIL,css;date:2018/08/18 00:00:00;