## Animation cùng CSS 2D transforms
Ở bài viết cũ mình đã chia sẽ về các methods để biến đổi một element như `translate`, `rotate`,... ([Ở đây nè](https://kipalog.com/posts/Tim-hieu-ve-CSS-2D-transforms)). Trong bài viết đó thì trông mấy cái đó chả có gì thú vị ngoài việc làm cho element trở nên dị dạng <i class='em em-sleeping'></i>. Cho nên trong bài này chúng ta sẽ vận dụng một số thứ đã có trước đó của CSS kết hợp với mấy cái transform này, xem nó thú vị tới đâu <i class='em em-laughing'></i>.
### Phù phép cho translate(), rotate(), skew() và scale()
Ở bài cũ mình cũng đã có đưa các vị dụ về sự chuyển đổi của các methods ở trên, nhưng chỉ nhìn hình ảnh của element sau khi bị chúng nó làm biến dạng thì cũng không thú vị lắm, vậy nếu chúng ta cho nó một tí chuyển động thì có vẻ hay hơn :3.

Trước hết để chúng ta sẽ dùng HTML tạo 4 box kế tiếp nhau tượng trưng cho 4 cái methods kia (đặt cạnh nhau sẽ dễ quan sát hơn)
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/44l47mdisg_image.png)
Và tinh chỉnh một tí CSS để 4 cái box trông dễ nhìn hơn
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/g8zgf6riik_image.png)
Ở đây 4 box mình đều viết CSS cho nó như nhau chỉ khác ở chỗ đổi màu thôi cho nên mình chỉ đưa ra phần `.showcase` với `box1` làm mẫu thôi :3. 4 cái box của chúng ta đây:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/2comj589ll_image.png)

Tiếp theo là phần quan trọng, chúng ta sẽ dùng `:hover` cùng với `transition` (transition này sẽ có bài giải thích sau, giờ chỉ cần biết nó làm mọi việc diễn ra mượt mà và chậm rãi hơn là được <i class='em em-laughing'></i>) Để tạo animation cho các box mỗi khi ta trỏ chuột vào như sau:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/v5ekvzaz8z_image.png)
Có một điều lưu ý là, để có thể có thể show transform được trên tất cả các trình duyệt thì chúng ta cần phải thêm 1 dòng dành riêng cho trình duyệt đó. Thay vì chỉ ghi một dòng là `transform:rotate(30deg)` (dòng này là standard syntax có thể chrome hiểu được nhưng các trình duyệt khác lại không hiểu được nên transform của chúng ta sẽ không thực hiện được). Chúng ta cần viết thêm các dòng như sau:
* Thêm `-webkit-`phía trước transform `-webkit-transform:rotate(30deg)` dành cho trình duyệt Safari
*  Thêm `-ms-`phía trước transform `-ms-transform:rotate(30deg)` dành cho trình duyệt IE 9 (Internet Explorer)
*   Thêm `-moz-`phía trước transform `-moz-transform:rotate(30deg)` dành cho trình duyệt con cáo lửa (Firefox <i class='em em-laughing'></i>)
*   Thêm `-o-`phía trước transform `-o-transform:rotate(30deg)` dành cho trình duyệt Opera

Ở các hình có code CSS minh họa mình sẽ không ghi vào để cho việc trích dẫn hình không bị quá dài, mình sẽ ghi nó đầy đủ vào phần code của Codepen nhé. Và đây là kết quả của chúng ta (rê chuột vào mỗi box để xem sau khi được **phù phép** thì chúng nó trông như nào)
<p data-height="265" data-theme-id="dark" data-slug-hash="mjJxdK" data-default-tab="css,result" data-user="tortoise10h" data-embed-version="2" data-pen-title="Animation with CSS transforms 1" class="codepen">See the Pen <a href="https://codepen.io/tortoise10h/pen/mjJxdK/">Animation with CSS transforms 1</a> 
Trông hiệu ứng phết rồi ấy nhỉ <i class='em em-laughing'></i>. Giờ cùng thử thêm một hiệu ứng nửa để cho đã mắt <i class='em em-laughing'></i>
Chúng ta sẽ lấy lại cái box1 kia và tạo hiệu ứng khác cho nó :3. Lần này chúng ta sẽ không chỉ "biến hình" nó mà sẽ cộng thêm tí hiệu ứng khác như chuyển màu background, border,...Chúng ta sẽ viết lại CSS cho box1 như sau:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/4n0z0434bz_image.png)
Cụ thể ở đây là sau khi chúng ta trỏ chuột vào box1 thì nó sẽ được zoom to lên nhờ `scale`, sẽ có thêm màu background và border của nó sẽ bị bẻ cong đi đôi chút <i class='em em-laughing'></i>
<p data-height="265" data-theme-id="dark" data-slug-hash="qyOQXj" data-default-tab="css,result" data-user="tortoise10h" data-embed-version="2" data-pen-title="Animation with CSS transforms 2" class="codepen">See the Pen <a href="https://codepen.io/tortoise10h/pen/qyOQXj/">Animation with CSS transforms 2</a> 
### Multiple transforms
Qua phần vận dụng transform ở trên chúng ta đã bắt đầu thấy nó cũng có thể làm ra được những thứ hay ho và lạ mắt chỉ với HTML và CSS rồi đúng không <i class='em em-laughing'></i>. Như đã nói ở bài trước chúng ta còn có thể vận dụng nhiều cái transform cùng một lúc, vậy thử làm xem nó có hay hơn không :v.

Tiếp tục lấy box1 ở trên để làm chuột thí nghiệm (quá lười để tạo cái mới <i class='em em-laughing'></i>). Tuy nhiên lần này chúng ta sẽ áp dụng 2 cái transform vào nó là `rotate` với mục đích là quay nó mòng mòng và kết hợp với `scale` để vừa quay vừa to lên :v. Ta có đoạn CSS như sau:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/4jzn8hwcxx_image.png)
Lần này cái box1 này sẽ được quay 360 độ cùng với việc được nhân 2 kich cỡ :v (mình có chỉnh transition lên 1.5s thay vì 1s để quay lâu hơn, xem đã hơn)
<p data-height="265" data-theme-id="dark" data-slug-hash="QBjJOX" data-default-tab="css,result" data-user="tortoise10h" data-embed-version="2" data-pen-title="Animation with CSS transforms 3" class="codepen">See the Pen <a href="https://codepen.io/tortoise10h/pen/QBjJOX/">Animation with CSS transforms 3</a> 

Hoặc chúng ta có thể làm thêm một ví dụ khác sinh động hơn. Trỏ chuột vào background màu xám để thấy sự kì diệu <i class='em em-laughing'></i> (các bạn xem code trong Codepen luôn nhé)
<p data-height="265" data-theme-id="dark" data-slug-hash="gjaQVy" data-default-tab="css,result" data-user="tortoise10h" data-embed-version="2" data-pen-title="Animation with CSS transform 4" class="codepen">See the Pen <a href="https://codepen.io/tortoise10h/pen/gjaQVy/">Animation with CSS transform 4</a>  

Ở ví dụ trên Nhìn hay hay đúng không nào <i class='em em-laughing'></i>. Và có rất nhiều các hiệu ứng hay khác mà mình chưa nêu được ở đây (một phần là mình lười, phần lớn hơn là mình nghĩ méo ra đó :v). Dựa trên mấy cái cơ bản ở 2 bài CSS 2D transform chúng ta còn có thể làm ra được nhiều cái hay hơn nửa <i class='em em-laughing'></i>. Các bạn có thể tham khảo link ở dưới hoặc tự chế thêm <i class='em em-laughing'></i>.
## Link tham khảo
Mình tham khảo ở:
* W3School [Ở đây](https://www.w3schools.com/css/css3_2dtransforms.asp)
* The art of web [Đây nè](https://www.the-art-of-web.com/css/css-animation/)



<<<<<Blog-Meta-Data>>>>>
title:Hiệu ứng "sinh động" cùng CSS 2D transforms;publishMode:publish;tags:coding,css;date:2018/08/23 00:00:00;