## CSS Box Model là gì?
Ở trong HTML với mọi element chúng ta có thể gọi nó là một cái "hộp". Và trong CSS thì thuật ngữ Box Model dùng để nói về design và layout. Chúng ta có thể coi CSS Box Model giống như là một cái hộp bao quanh element của chúng ta và trong đó có rất nhiều lớp dày mỏng khác nhau, các lớp dày mỏng đó bao gồm: margins, border, padding và cuối cùng là phần nội dung của chúng ta (text và ảnh). Chúng ta có thể xem hình dưới đây để dễ hình dung hơn về Box Model:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/k68zn5q971_image.png)
* **Content:** như đã nói ở trên đây là phần mà text và hình ảnh của chúng ta xuất hiện
* **Padding:** là một khoảng trống kế tiếp bọc xung quanh **content**
* **Border**: phần khung bao bọc xung quanh **padding** và **content**
* **Margin**: cuối cùng, **margin** là phần ngoài cùng của Box Model, chỉ là một khoảng trống không màu

Tiếp theo chúng ta sẽ đi đến từng phần một của một Box Model để hiểu rõ hơn về tính chất cũng như cách tính toán chính xác cho một Box Model
### Content
Tiếp tục nhắc lại **content** là phần xuất hiện của text và hình ảnh, phần này không có gì đặc biệt để nói cho lắm, tổng kích cở của text bao nhiêu (có thể lớn nhỏ nếu chúng ta tùy chỉnh `font-size`) hay hình ảnh bao lớn thì đó cũng là kích cở của **content**. Tuy nhiên, có một điều cần chú ý là **content** và hai thuộc tính **height** và **width**, khi chúng ta đặt một **height** hay một **width** hoặc thậm chí cả hai cho một element thì **height** và **width** này **chỉ tác động lên một vùng duy nhất đó là content chứ không hề đá động gì đến padding, border hay margin cả.** Vậy, phần kích thước đầu tiên của Box Model đó chính là content.
### Padding
Nói đơn giản về **padding** thì nó là thuộc tính dùng để tạo ra một vùng khoảng trống bao bọc xung quanh **content** và nó sẽ nằm bên trong **border**. Khi xét padding cho một element ta có thể xét theo 2 kiểu:
* Xét theo từng bên của element: top, right, bottom và left như sau:
	+ padding-top
	+ padding-right
	+ padding-bottom
	+ padding-left
* Hay là xét theo kiểu viết tắc:
	+ padding: 5px  6px   8px    7px
			 (top right bottom left)
	+ padding:  5px     6px     7px
			  (top  right&left  bottom)	
	+ padding:      5px        6px
			  (top&bottom right&left)
	+ padding: 5px (cho toàn bộ 4 mặt)

Và chúng ta có các đơn vị để xét **padding** như:
* "Đơn vị đo chiều dài" như: cm, px, em, etc
* Phần trăm (%): cái % này sẽ phụ thuộc vào **width** của thằng element chứa nó
* Inherit: kế thừa cái **padding** đã được xét ở element mẹ (hay bố cũng được)

Có một điều cần lưu ý nữa là giữa **padding** và **width**. Ví dụ chúng ta cho một thằng `div`với thuộc tính như sau:
```
div{
	width:350px;
    padding:25px;
}
```
Thì như đã nói ở trên thằng **width** là chỉ xét cho mỗi phần **content** có nghĩa là giờ phần **content** của mình nó dài 350px chưa kể **padding**. Vậy để tính được hết chiều dài của cái `div` này thì mình phải cộng thêm 50px nửa (25px padding bên trái và 25px padding bên phải) => tổng chiều rộng của cái `div` là 400px.
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/aj7pasxma5_image.png)

### Border
**Border**, lớp tiếp theo của Box Model, bỏ qua các phần trang trí màu mè của nó, chúng ta chỉ xét tới các phần như `border-width` hay xét border cho các mặt của element. Thứ nhất, nói sơ qua cấu trúc **border** thì nó sẽ gồm có:
* `border-width`: độ rộng của border tính bằng các đơn vị như: in px, pt, cm, em, etc
* `border-style`: style cho border như kiểu đường thằng, chấm bi, song nét,... (solid, dotted, double,.. )
* `border-color`: màu cho border và được xét bởi nhiều cách: tên màu, giá trị hexa, giá trị rgb hay là trong suốt (transparent)

Hoặc cả đống trên có thể ghi tắc lại thành `border: chiềurộng kiểu màu` ví dụ `border:2px solid black`, đó là xét cho tất cả 4 phía: top, right, bottom và left, nếu muốn chúng ta có thể xét riêng cho từng phía với từng kiểu như sau:
 *  `border-top`
 *  `border-right`
 *  `border-bottom`
 *  `border-left`

Việc xét cho toàn bộ **border** hay xét cho từng phía sẽ gây ảnh hưởng khác nhau đến Box Model, lấy lại ví dụ ở padding lúc nãy
```
div{
	width:350px;
    padding:25px;
}
```
Như trên là chúng có ta một `div` với chiều rộng là 400px nếu chúng ta thêm vào dòng `border:5px solid orange` thì chiều rộng của `div` sẽ lên là 410px vì nó được cộng thêm 5px của border bên trái và 5px của border bên phải. Tuy nhiên, nếu ta chỉ thêm vào `border-left:5px solid orange` thì chiều rộng của `div` chỉ là 405px vì chỉ có 5px của border trái còn bên phải thì làm gì có mà thêm.
### Margin
Lớp cuối cùng của Box Model đó chính là lớp **margin** bên ngoài, **margin** là một thuộc tính dùng để tạo khoảng cách xung quanh element để cách element đó với các thứ khác và phần **margin** sẽ nằm bên ngoài **border**. Giống như **padding** thì **margin** cũng được xét theo hai kiểu, một là: 
* margin-top
* margin-right
* margin-bottom
* margin-left

Và thứ hai là viết tắc tương tự như **padding**. Về phần đơn vị, **margin** cũng có các kiểu: "đơn vị đo độ dài", % hay inherit như **padding**. Tuy nhiên, margin còn có thêm một giá tị nửa, đó chính là `margin:auto`. Khi ta dùng cái `auto` này thì trình duyệt sẽ tự động tính toán và đặt lại khoảng cách cho element sao cho nó được căn ngay chính giữa bên trong container chứa nó. 

Một vấn đề cuối cùng của **margin** đó là **margin collapse**, chúng ta sẽ đưa ra một ví dụ để có thể dễ dàng giải thích. Ví dụ: Chúng ta sẽ cho 2 element `h1` và `h2` nằm trong một `div` có class là "left" như sau:
```
<div class="left">
	<h1>Hello</h1>
    <h2>Holle</h2>
</div>
```
và tiếp tục ta sẽ cho element `h1` với `margin-bottom` là 50px và element `h2` với `margin-top` là 20px.
```
div.left h1{
	margin-bottom:50px;
}
div.left h2{
	margin-top:20px;
}
```
Nếu như xem ở trên xong chúng ta sẽ nghĩ rằng 2 thằng `h1` và `h2` này sẽ cách nhau là 70px (50px + 20px). Tuy nhiên, do cậu **margin collapse** này mà 2 element `h1` `h2` của chúng ta chỉ cách nhau có 50px
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/nglw37k6y9_image.png)
Để rõ ràng, chúng ta sẽ viết thêm một `div` khác với class là "right" và vẫn với 2 dòng HTML  của `h1` và `h2` kia. Tuy nhiên, chúng ta sẽ chỉ cho `h1` có `margin-bottom` là 70px để so sánh.
```
div.right h1{
	margin-bottom:70px;
}
```
Và đây là kết quả của chúng ta:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/kwo6glfo3a_image.png)
Như chúng ta đã thấy, bên phía class "left" mặc dù có cả `margin-bottom:50px` của `h1` và `margin-top:20px` của `h2` nhưng khoảng cách vẫn chỉ là 50px bé hơn so với khoảng cách một `margin-bottom:70px` của `h1` bên  class "right". Đó chính là **margin collapse**.

Tóm lại, dựa trên kiến thức của Box Model, nếu ta chúng ta có một element `div` chẳng hạn được viết như thế này:
```
div{
	background-color:#1abc9c;
	width:300px;
    padding:30px;
  	border:10px solid black;
	margin:20px;
}
```
*Lưu ý đã có chỉnh `background-color` của `body` sang màu #e0e0e0*
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/343pz4v74t_image.png)

Thì độ rộng của nó sẽ là 420px được tính như sau: (tạm gọi là total)
total = `width` + `right padding` + `left padding` + `right border` + `left border` + `right margin` + `left margin`
total = 300px + 30px + 30px + 10px + 10px + 20px + 20px = 420px.
Đây là một kiến thức quan trong chúng ta cần hiểu rõ để áp dụng vào tạo layout web hay để sau này khi code HTML và CSS sẽ không bị bối rối trong lúc code khi chạm phải mấy cái này :3.
## Link tham khảo
* Height and width [Ở đây](https://www.w3schools.com/css/css_dimension.asp)
* Padding [Ở đây](https://www.w3schools.com/css/css_padding.asp)
* Borders [Ở đây](https://www.w3schools.com/css/css_border.asp)
* Margins [Ở đây](https://www.w3schools.com/css/css_margin.asp)
* Box Model [Ở đây](https://www.w3schools.com/css/css_boxmodel.asp)



<<<<<Blog-Meta-Data>>>>>
title:Cấu trúc CSS Box Model;publishMode:publish;tags:coding,css;date:2018/08/28 00:00:00;