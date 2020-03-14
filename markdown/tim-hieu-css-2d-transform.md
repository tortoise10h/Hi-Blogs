## Chút lý thuyết về CSS 2D transforms
**CSS 2D transforms**, tác dụng thì như cái tên của nó - "biến hình" cho các element theo chiều 2D (còn 3D nửa, 4D chưa biết <i class='em em-laughing'></i>). Cái **CSS 2D transform** này cho phép chúng ta tác động lên element để có thể thay đổi vị trị, hình dáng hay xoay nó mòng mòng :v. Để làm được mấy điều đó chúng ta có một số methods như sau:
* `translate(x,y)`: có tác dụng là dịch chuyển vị trí của element sang trái, phải, rồi lên trên, xuống dưới với `x` là dịch theo chiều ngang còn `y` là dịch theo chiều dọc (như trục tọa độ Oxy ấy :v) đơn vị là px, em,...
* `rotate(?deg)`: công dụng của cái này là giúp ta xoay element với góc độ tự chọn `?deg` (deg là kí kiệu của độ: **degrees**) và có thể xoay theo chiều kim đồng hồ (độ là số dương) hoặc ngược kim đồng hồ (độ là số âm) tùy thích.
* `scale(x,y)`: công dụng của  nó vô cùng đơn giản là **zoom**, nó dùng để zoom element to lên hoặc nhỏ lại tùy chỉnh với `x` là zoom chiều ngang và `y` là zoom chiều dọc, ở đây không cần ghi đơn vị, nó tính theo tỉ lệ so với element ví dụ 1 là giữ nguyên 2 là tăng lên gấp đôi, vân vân mây mây
* `skew(x,y`: công dụng của nó là là làm **nghiêng**  cho element (lát xuống ví dụ để dễ hiểu hơn). Thực ra là có chia ra `skewX()` và `skewY` nhưng chỉ cần ghi `skew` là có thể chỉnh được cả X và  Y rồi (vậy tiện hơn).

Thực ra còn một cái `matrix` tuy nhiên nó cũng chỉ là tổng hợp giữa `scale` `skew``translate` và nhìn hơi rối nên mình không nhắc (tại mình ghét nó đấy, đã ghét tuổi gì vào <i class='em em-angry'></i>)
### Translate
Ở đây chúng ta có một thẻ `div` như sau:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/f0ijnh4up7_image.png)
Và đây là kết quả của nó:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/9wh6fd06uf_image.png)
Chúng ta có một hình chữ nhật nằm ở góc trái bên trên của ảnh, bây giờ chúng ta muốn thay đổi vị trí của nó đi, ta làm như sau:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/bq9kjuw5jm_image.png)
Và vị trí của nó đã bị di chuyển, cụ thể là sang phải 100px sau đó thụt xuống dưới 200px
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/5rofue04cp_image.png)
Đó là cách hoạt độn của `translate`
### Rotate
Tiếp tục sử dụng hình chữ nhật ở trên nhưng ta bỏ đi phần `translate` và thay vào đó là `rotate` để xem nó hoạt động như thế nào :3.
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/oecies30o7_image.png)
Ở đoạn CSS trên ta chọn `transform:rotate(40deg)` tức là ta sẽ xoay hình chữ nhật lúc nãy về phía bên phải 40 độ (nhắc lại số dương là cùng chiều kim đồng hồ còn số âm là ngược lại). Và kết quả:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/vnhue64lv8_image.png)
### Scale
Tiếp đến là `scale` chúng ta sẽ cho một hình chữ nhật nhỏ  và dùng scale để tăng tỉ lệ nó lên
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/5iadgp2ssk_image.png)
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/bd7qntbk46_image.png)
Chúng ta sẽ dùng `scale` và tăng tỉ lệ của hình chữ nhật lên gấp đôi:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/uoe9jtp0ap_image.png)
Và kết quả là nó đã to lên gấp đôi (to lên ở đây bao gồm tất cả những thứ trong thẻ `div`của chúng ta từ font chữ, border cho đến kích thước: chiều cao, chiều rộng)
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/glm884srgg_image.png)
### Skew
Để giải thích cho cái khái niệm về `skew` mà mình nêu ở trên, chúng ta có thể quan sát ví dụ để dễ hiểu hơn. Chúng ta sẽ đi vào `skewX` và `skewY` sau đó thì đi đến `skew` cho dễ hiểu, Ví dụ ta vẫn lấy lại cái hình chữ nhật ở phần `translate` (mình lười trích lại code <i class='em em-laughing'></i>) 
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/1vdo1hh8ao_image.png)
Sau đó nếu ta áp dụng `skewX` vào:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/h1jkt3weuv_image.png)
Thì ta sẽ được như này:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/1jlrxvp9ez_image.png)
Đây là cái **nghiêng** mà mình muốn nói. Dĩ nhiên chúng ta hoàn toàn có thể **nghiêng** theo hướng ngược lại bằng cách đổi độ thành số âm.
Tiếp theo, nếu ta dùng `skewY` thì sao?
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/8ao7u8etbj_image.png)
 Thì hình chữ nhật ban đầu sẽ thành ra như này:
 ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/fs78vql8l4_image.png)
 Nó nghiêng lên trên <i class='em em-laughing'></i>
 Và cuối cùng là `skew` (lưu ý trong `skew` sẽ bao gồm cả `skewX` và `skewY` số đầu là x số sau là y và nếu chúng ta chỉ ghi 1 số trong `skew` thì nó sẽ tự động hiểu số đó là x còn thằng y sẽ bị cho là 0). Chúng ta hãy thử ví dụ này lên hình chữ nhật ban đầu
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/h0ckojn1t7_image.png)
Và đây là kết quả:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/jk3nudkn4j_image.png)
Nó nghiêng bốn bề <i class='em em-laughing'></i> 

Thêm nửa là chúng ta có thể áp dụng nhiều cái transform (như `translate`, `skew`,...) vào chung với nhau bằng cách đặt chúng cách nhau 1 khoảng trắng . Chẳng hạn như dưới đây là mình gắn cả `rotate` `skew` và `scale` vào hình chữ nhật với chữ như sau:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/5qv8h2dnc_image.png)
áp dụng mutiple transform vào:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/f9ymb2bsjx_image.png)
Ta sẽ được một hình trông vui hơn <i class='em em-laughing'></i>
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/4opd12iife_image.png)

thoạt nhìn thì thấy mấy cái này có vẻ không vui, tuy nhiên nó cũng có thể dùng làm một số hiệu ứng khá là hay, mình sẽ viết ở bài sau, tới đây lười quá <i class='em em-laughing'></i>
## Link tham khảo
Nơi mình tham khảo:
* W3school [Ở đây](https://www.w3schools.com/css/css3_2dtransforms.asp)

<<<<<Blog-Meta-Data>>>>>
title:Tìm hiểu về CSS 2D transform;publishMode:publish;tags:TIL,css;date:2020/03/14 17:53:05;