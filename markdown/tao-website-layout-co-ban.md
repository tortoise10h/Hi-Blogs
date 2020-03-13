## Website layouts
Như chúng ta biết, bố cục của một website sẽ được chia ra thành nhiều phần, các phần chính đáng chú ý nhất là:
* **Header**: Tiêu đề của trang web, thường thì đây là chỗ của logo website
* **Navigation Menu**: Đây là phần menu điều hướng, giúp cho người đọc có thể truy cập vào các phần khác nhau của trang web
* **Content**: Đây là phần chứa nội dung chính của trang web, cũng có thể là nơi hiển thị quảng cáo của website (thường thì nằm ở hai bên website và ở giữa là nội dung bài viết)
* **Footer**: Đây là phần cuối của website, thường là nơi chứa tên của cá nhân hoặc tổ chức sở hữu website và cũng là nơi chứa thông tin bản quyền. Một số website có thể cho vào navigation link ví dụ như *About*,  *Contact*, *Help*  vân vân mây mây

Chúng ta có thể xem hình ảnh dưới đây để hiểu rõ hơn về cấu trúc cơ bản của một trang web (nó có thể có nhiều biến thể khác không tuân theo trật tự sắp xếp này, tuy nhiên đây là layout cơ bản nhất và có khá nhiều website dùng)
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/6kdz4tnaud_image.png)
## Tạo  layouts cơ bản
### Định hình website
Trước khi muốn tạo ra được một website với các phần nội dung chia 3 xẻ 7, phân trái bổ phải thì chúng ta cần xác định trước cấu cúc của website mà mình cần tạo, cần phải vẽ ra và xác định rõ vị trí cần bố trí các nội dung thế nào, dài rộng là bao nhiêu (tốt nhất là vẽ ra giấy, xấu cũng được nhưng nó giúp ta nhìn theo và code dễ dàng hơn). Ở đây chúng ta thiết kế theo bố cục của hình trên.
### Tạo "xương sống" cho trang web
Con người cần phải có bộ xương thì web cũng vậy nó cũng cần có một "bộ xương" HTML trước khi muốn tô điểm thêm màu mè cho nó. Chúng ta bắt đầu viết HTML cho web nào.
#### Header
Như ở trên Header là *"Tiêu đề của trang web, thường thì đây là chỗ của logo website"*, ở đây chúng ta có thể chọn hình ảnh hay chữ làm tiêu đề tùy thích, mình chọn chữ cho đơn giản
```
<header>
	<h1>This is my branding</h1>
    <p>Say something about website</p>
</header>
```
Và đây là kết quả thu được:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/3rtf4b2bgp_image.png)
trông cũng ổn phết <i class='em em-laughing'></i>:laughing:. Tiếp tục tới phần tiếp theo nào
#### Navigation Menu
Tiếp theo là tạo một thanh menu điều hướng cho người dùng dễ dàng thao tác hơn.  Ở đây chúng ta dùng `nav` là một thẻ chuẩn HTML5 để tạo navigation menu
```
<nav>
	<ul>
		<li><a href="#link">Home</a></li>
		<li><a href="#link">News</a></li>
		<li><a href="#link">About</a></li>
	</ul>
</nav>
```
Ta dùng combo `ul` và `li`để tạo ra các mục có trong thanh menu, nếu muốn thêm mục thì chỉ cần thêm một dòng `li` vào là được.
Kết quả:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/hqe9vmxt1e_image.png)
Cũng có thể xem như là một menu rồi đấy chứ <i class='em em-laughing'></i> 
#### Content
Sau khi có được phần "biển hiệu" và thanh menu, tiếp theo chúng ta tiếp tục tạo nội dung cho trang web. Ở đây ta dùng `section` để xác định phần này là nội dung chính của trang web và dùng `article` để chứa các phần nội dung nhỏ bên trong bao gồm nội dung bài viết, quảng cáo, etc. Giả sử ở đây chúng ta có 3 phần nội dung như hình trên. Vì đây là tạo layouts cơ bản nên chúng ta sẽ tạo 3 cột bằng nhau chứ không chia nhỏ lớn như hình trên (làm vậy cho nhanh đấy :v)
```
<section>
	<article>
		<h1>Column</h1>
		<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas sit amet pretium urna. Vivamus venenatis velit nec neque ultricies, eget elementum magna tristique. Quisque vehicula, risus eget aliquam placerat, purus leo tincidunt eros, eget luctus quam orci in velit. Praesent scelerisque tortor sed accumsan convallis.</p>
	</article>
	<article>
		<h1>Column</h1>
		<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas sit amet pretium urna. Vivamus venenatis velit nec neque ultricies, eget elementum magna tristique. Quisque vehicula, risus eget aliquam placerat, purus leo tincidunt eros, eget luctus quam orci in velit. Praesent scelerisque tortor sed accumsan convallis.</p>
	</article>
	<article>
		<h1>Column</h1>
		<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas sit amet pretium urna. Vivamus venenatis velit nec neque ultricies, eget elementum magna tristique. Quisque vehicula, risus eget aliquam placerat, purus leo tincidunt eros, eget luctus quam orci in velit. Praesent scelerisque tortor sed accumsan convallis.</p>
	</article>
</section>
```
Đây là kết quả của đống code trên
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/6tv6t12ed0_image.png)
Ơ tại sao nó lại không chia ra nhỉ? Đây chỉ mới là khung xương cho nó thôi <i class='em em-laughing'></i> chúng ta sẽ chỉnh hình nó bằng CSS sau
#### Footer
Cuối cùng là phần cuối của một trang web cơ bản *" thường là nơi chứa tên của cá nhân hoặc tổ chức sở hữu website và cũng là nơi chứa thông tin bản quyền"*
```
<footer>
	<p>HyHy &copy; 2018</p>
</footer>
```
kết quả:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/cbq76j0wqj_image.png)
Hãy cùng xem lại sau tất cả đống code ngoằn ngoèo trên kia chúng ta đã có được gì
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/rln4qa0mmb_image.png)
Nhìn khá là thô đúng không, bởi vì nó là "xương" mà. Chúng ta tiến hành gắn da thịt cho nó đỡ thô hơn thôi nào!
### Làm đẹp bằng CSS
#### Header
Đây là phần biển hiệu, chúng ta sẽ làm nó trở nên màu mè và to lớn hơn một tí để dễ quản bá tên tuổi hơn
```
header{
	background-color:lightgrey;
	padding:1.5em;
	text-align:center;
}
```
Và:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/n047zxmep9_image.png)
Bằng việt thêm `background-color`  và đưa text ra giữa "biển hiệu" đã nhìn trông ổn hơn :3
#### Navigation Menu
Đây là một phần khá là lằng nhằng (chủ yếu do nó dài <i class='em em-laughing'></i>). Để làm một thanh menu đơn giản từ 3 cái list xí xấu hồi nãy chúng ta cần bỏ đi phần bullet phía trước nó và đưa nó về một hàng ngang và cộng thêm tí màu mè nửa.
```
/*màu cho thanh menu */
nav{
	background-color:#1abc9c;
}
/*chỉnh đốn vị trí và loại bỏ đống bullet phía trước các mục trong li*/
nav ul{
	margin:0;
	padding:0;
	list-style-type:none;
}
/*đưa các mục về hàng ngang*/
nav li{
	display:inline-block;
}
/*trang điểm*/
nav li a{
	display:inline-block;
	text-decoration:none;
	color:white;
	padding:14px 16px;
}
```
và hãy xem cái list xí xấu lúc nãy như thế nào rồi
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/r0vv98ybw3_image.png)
Tada! Đúng như ta mong muốn, nó đã 1 hàng, đã bỏ được đống bullet phía trước và còn có thêm màu mè. Ta cần thêm một tí hiệu ứng lúc rê chuột vào (để còn biết mình đang chọn cái nào nửa ==!)
```
nav li:hover{
	background-color:orange;
}
```
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/feh93kxplq_image.png)
#### Content
Như đã nói ở trên, chúng ta sẽ chia 3 cột này thành 3 cột bằng nhau và nằm trên cùng một hàng
```
*{
	box-sizing:border-box;
}
/*tạo tí màu mè cho phần content*/
section{
	background-color:lightgrey;

}
/*chia cột thành 3 phần và làm nó trên cùng một hàng*/
article{
	width:33.33%;
	float:left;
	background-color:#f0f0f0;
	padding:1em;
}
section:after{
	content:"";
	clear:both;
	display:table;
}
```
Kết quả:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/rh4raz004r_image.png)
#### Footer
Phần này thì việc trang trí cũng khá giống với phần Header ở trên
```
footer{
	background-color:black;
	padding:0.8em;
	color:white;
	text-align:center;
}
```
Kết quả:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/6689jhayp6_image.png)

Và tổng quan lại sau khi đã trang điểm bằng CSS thì website của chúng ta đã có chút thay đổi (không hẳn là đẹp, chắc tại thẩm mĩ mình kém quá)

**Trước**
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/rln4qa0mmb_image.png)

**Và sau**
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/tmqmrnw1n7_image.png)

Chưa được đẹp lắm, nhưng có vẻ cũng đúng được yêu cầu đề ra :v. Chí ít nó cũng là một kiến thức cơ bản để có thể làm nền cộng với sự sáng tạo làm ra nhiều layouts khác đẹp hơn

## Link tham khảo
Vì mình đang học HTML + CSS ở W3School nên link vẫn là [ở đây nha](https://www.w3schools.com/css/css_website_layout.asp)



<<<<<Blog-Meta-Data>>>>>
title:Tạo website layout cơ bản;publishMode:publish;tags:coding,html,css;date:2018/08/11 00:00:00;