## Sơ lược về CSS Flex-box
Trước Flex-box layout module thì chúng ta có các kiểu layout như: **Block** dành cho các phần, đoạn trong một trang web, **inline** dành cho phần text,.... Nếu trước kia chúng ta muốn tạo được một trang web với layout cơ bản như là có phần **branding**, rồi **thanh menu**, tiếp đến là phần **content** cuối cùng là phần **footer** thì chúng ta cần phải làm rất nhiều thứ: nào là float qua trái qua phải hay chỉnh position,bla bla bla,.. thì giờ với flex-box chúng ta sẽ dễ dàng làm hơn không cần phải cực khổ như trước nữa (tuy nhiên vẫn cần tí nổ lực <i class='em em-laughing'></i>).

Đây là các phiên bản browser khác nhau hổ trợ cho flex-box: (tham khảo để khỏi hoảng hốt khi code mình lại sai trên máy người ta chỉ vì do người ta xài phiên bản cũ không hỗ trợ <i class='em em-laughing'></i>)
 ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/m96hqfnefh_image.png)
 
Để bắt đầu sử dụng flex-box thì chúng ta cần phải xây dựng được cấu trúc của nó, dưới đây là ví dụ: 
```
.flex-container{
	display:flex;
    background-color:#1abc9c;
}
.child{
  background-color: #f1f1f1;
  margin: 10px;
  padding: 20px;
  font-size: 20px;
}
```
Phần code ở trên là một ví dụ về một cấu trúc khi ta dùng flex-box (để dễ hình dung) , nó sẽ chia ra làm 2 phần đó là **parent** (class `flex-container`) và **items** (class `child`) với phần **parent** chúng ta cần phải có `display:flex` để thể hiện là chúng ta đang sử dụng flex-box layout module. Và tiếp theo là phần **items** sẽ được viết bên trong parent để tạo ra các ô tùy ý. Ví dụ ta có một đoạn code `html` tiếp nối theo đoạn CSS ví dụ ở trên:
```
<div class="flex-container">
	<div class="child">1</div>
	<div class="child">2</div>
	<div class="child">3</div>
	<div class="child">4</div>
</div>
```
Thì đây là kết quả:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/ay6yxpvbya_image.png)
Quá dễ dàng  để tạo ra layout mà không cần phải float hay gì gì cả. Ở hình trên với phần **parent** chúng ta sẽ thấy đó là phần có background màu xanh đã được ta đặt ở trên cùng với `display:flex`để các **items** bên trong hiển thị thành từng ô riêng.

Nói nãy giờ thì ta dễ dàng thấy cấu trúc của chúng ta sẽ xoay quay 2 thằng đó là **parent** và **items**, chính vì vậy nên chúng ta sẽ đi đến với các property dành riêng cho từng thằng và dùng các property đó để tạo nên một layout website dễ dàng hơn. Trong phần này chúng ta sẽ nói đến các property của phần **parent**
## Các property parent
### flex-direction
**flex-direction** property dùng để thiết lập trục chính của **parent** (ngang hay dọc) và đặt các **items** bên trong nằm theo chính hướng đó . **flex-direction** có 4 giá trị đó là: 
* **row**: đây là kiểu mặc định, các **items** sẽ nằm theo chiều ngang từ trái sang phải giống như text.
* **row-reverse**: cũng là sắp xếp các **items** bên trong nằm theo chiều chiều ngang, tuy nhiên nhiên là thứ tự từ phải sang trái và vị trí của nó cũng sẽ bị đảo lại. Chúng ta lấy lại ví dụ hình ở trên và cho thêm vào `flex-direction:row-reverse` thì sẽ được như sau: ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/fvz862w17e_image.png)
* **column**: trái ngược với **row** thì chính là **column**, các **items** bên trong bây giờ sẽ theo chiều dọc thứ tự từ trên xuống dưới, đây là ví dụ khi sử dụng `flex-direction:column`: ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/zb11cbd5kx_image.png) (*hình trên đã có thêm phần chiều rộng của các items là 50px để cho nó không bị trải dài ra*)
* **row-reverse**: cũng giống như **row** là nằm theo chiều dọc tuy nhiên các items sẽ đảo ngược vị trí lại với nhau (tương tự cách **row-reverse** làm với **row**).

Hình minh họa cho 4 giá trị của **flex-direction** <i class='em em-laughing'></i> 
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/grznx52dq5_image.png)
### flex-wrap
Để hiểu về **flex-wrap**, chúng ta hãy xem ví dụ dưới đây: (thu nhỏ browser lại để thấy sự khác biệt giữa hai ví dụ)
Ví dụ 1: có sử dụng `flex-wrap:wrap`
<p data-height="265" data-theme-id="dark" data-slug-hash="WKXQVP" data-default-tab="html,result" data-user="tortoise10h" data-pen-title="flex-wrap example" class="codepen"> <a href="https://codepen.io/tortoise10h/pen/WKXQVP/">flex-wrap example</a> 
Ví dụ 2: sử dụng `flex-wrap:nowrap` hay đó chính là default
<p data-height="265" data-theme-id="dark" data-slug-hash="djZGyz" data-default-tab="html,result" data-user="tortoise10h" data-pen-title="flex-wrap example2" class="codepen"> <a href="https://codepen.io/tortoise10h/pen/djZGyz/">flex-wrap example2</a>

Sau khi xem 2 ví dụ ở trên chúng ta đã có thể hiểu được công dụng của **flex-wrap** là như thế nào. Khi sử dụng **flex-wrap** chúng ta sẽ quyết định xem các **items** bên trong **parent** là sẽ nằm ở trên 1 đường thằng hay là nhiều đường thẳng, nếu là nằm trên nhiều đường thằng thì nó sẽ hình thành nên một trục chéo để xác định khi ta resize lại browser (nhỏ hơn) thì các items sẽ nằm chồng lên nhau như thế nào.  **flex-wrap** có 3 giá trị đó là:
* **wrap**: khi sử dụng giá trị này, như chúng ta thấy ở trên khi resize browser nhỏ lại các **items** bên trong sẽ rơi xuống dòng và chồng lên nhau thành nhiều cột tùy thuộc vào độ nhỏ của browser mà ta đã resize.
* **nowrap**: giá trị này là default, khi sử dụng nó hoặc không dùng đến flex-wrap, nếu chúng ta resize browser nhỏ lại thì các items bên trong sẽ bị che khuất từ từ.
* **wrap-reverse**: khi ta dùng giá trị này, cũng như **wrap** nếu resize browser nhỏ lại các **items** sẽ chồng lên nhau, tuy nhiên vị trí của các **items** xếp sau sẽ được đưa lên đầu nếu ta sử dụng **wrap-reverse**.

### flex-flow
Property này đơn giản là viết tăc, gom cả **flex-direction** và **flex-wrap** lại với nhau. Nếu bình thường ta viết như thế này:
```
.flex-container{
	display:flex;
    flex-direction:row;
  	flex-wrap:wrap;
}
```
Thì dùng **flex-flow** để viết tắc lại sẽ ngắn hơn:
```
.flex-container{
    display:flex;
    flex-flow:row wrap;
}
```
Nếu ta bỏ trống cái nào thì cái đó coi như sẽ ở giá trị default.
### justify-content
**justify-content** property dùng để căn chỉnh các **items** bên trong **parent** theo chiều trục chính của nó (trục chúng ta đã đặc ở **flex-direction** là ngang hoặc dọc). **justify-content** có các giá trị như sau:
* **center**: giá trị này dùng để căn chỉnh các **items** bên trong sẽ nằm ở giữa container **parent**. Ví dụ ta dùng `justify-content:center` với trục hàng ngang thì sẽ như thế này: ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/7i9juitgxl_image.png) (*các items đã nằm ở giữa*) và nếu dùng cho trục dọc thì sẽ như này: ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/2n9ld9cy7l_image.png)
* **flex-start**:  **flex-start** là giá trị default, dùng để căn các **items** nằm về phía đầu trục, nếu là trục nganng thì là bên trái và trục dọc thì là ở trên
* **flex-end**: ngược lại với **flex-start** thì **flex-end** dùng để căn các **items** nằm về phía cuối trục, trục ngang là bên phải và trục dọc là ở dưới. 
* **space-around**: các **items** trên trục sẽ được cấp các khoảng trống bằng nhau: ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/1iqft2n73_image.png)
* **space-between**: các **items** trên trục sẽ được phân bố đều trên trục, item đầu sẽ nằm đầu bên trái trục và item cuối sẽ nằm  đầu bên phải trục: ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/5q7xhb2pp4_image.png)

Đây là hình tổng quát, minh họa cho các giá trị ở trên:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/mylavdywn2_image.png) (*Nguồn từ CSS-tricks*)
### align-items
với **align-items** chúng ta có thể hình dung nó giống như **justify-content** nhưng là phiên bảng dành cho trục chéo (nghĩa là hướng vuông góc với trục chính, nếu trục chính là ngang thì nó sẽ căn chỉnh theo hướng dọc ). **align-items** có các giá trị sau:
* **flex-start**: căn các **items** ra đầu trục chéo
* **flex-end**: căn các **items** ra cuối trục chéo
* **center**: căn các **items** ra giữa trục chéo
* **baseline**: các **items** sẽ được căn như thế này: ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/fetgg4xu0v_image.png)
* **stretch**: đây là giá trị default, các **items** sẽ bị kéo giãn ra cho đủ chiều dài của container, nếu chúng ta không đặt chiều cao cho các **items**: ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/z8td80hpds_image.png)

Hình minh họa cho các giá trị ở trên:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/cz8tyetf51_image.png) (*Nguồn CSS-tricks*)
### align-content
**align-content** có các giá trị như sau: **center, flex-start, flex-end, space-around, space-between và stretch**. Để dễ hiểu về phần này, dưới đây là ta có một hình ảnh ví dụ:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/f8s14shanh_image.png)
* Hình trên chính là giá trị default của **align-content**  chính là **stretch** các **items** sẽ bị kéo dài để đủ lấp vào chiều cao của container.
* Tiếp theo nếu chúng ta dùng `align-content:center` thì:![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/ccxk9s6urq_image.png) các **items** sẽ được căn chính giữa container parent
* Tiếp nữa nếu ta dùng `align-content:flex-start` ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/rh8pfioon5_image.png)
* Còn nếu ta dùng `align-content:flex-end` ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/v3o042bijw_image.png)
* Nếu ta dùng `align-content:space-around` thì nó sẽ như này ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/3b7rj2hhvh_image.png)
* Và cuối cùng là `algin-content:space-between` ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/w0aa0o08lg_image.png)
Đó chính là các property quan trọng trong phần **parent** để tạo layout dễ dàng hơn, phần sau chúng ta sẽ đi tới các property cho **items**

## Link tham khảo
* W3School [ở đây](https://www.w3schools.com/css/css3_flexbox.asp)
* CSS-tricks [ở đây](https://css-tricks.com/almanac/properties/a/align-content/) (đây là phần link của **align-content** kéo xuống dưới sẽ thấy phần related với các property khác)


<<<<<Blog-Meta-Data>>>>>
title:CSS Flexbox phần 1: Parent;publishMode:publish;tags:TIL,css;date:2018/09/03 00:00:00;