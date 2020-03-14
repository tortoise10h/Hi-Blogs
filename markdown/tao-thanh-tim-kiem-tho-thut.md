Trong bài viết này chúng ta sẽ tìm hiểu việc tạo ra một thanh tìm kiếm và khi nhấp chọn vào sẽ có hiệu ứng từ từ dài ra và từ từ thu ngắn lại khi bỏ chọn giống như gậy như ý của Tề Thiên Đại Thánh :v

## Tạo thanh tìm kiếm đơn giản
Trước hết chúng ta cần phải tạo được một thanh tìm kiếm đơn giản với HTML:
```
<form>
    	<input type="text" name="search" placeholder="Search..">
</form>
```
Kết quả chúng ta sẽ có được một thanh tìm kiếm như sau ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/ognjlm2oot_Capture.PNG)
Đây là một thanh tìm kiếm bình thường tạo bởi  thẻ `<form>` của html với thuộc tính placeholder để có được chữ "*Search...*" bên trong khung tìm kiếm
###"Trang điểm" thanh tìm kiếm bằng CSS
Trước khi đi đến tạo hiệu ứng cho thanh tìm kiếm thì ta sẽ tiến hành "trang điểm" cho nó một tí bằng CSS 
```
	input[type="text"] {
      width: 130px;
      box-sizing: border-box;
      border: 1px solid black;
      border-radius: 4px;
      outline:none;
      padding: 12px 14px;
	}
```
Sau đoạn code CSS trên ta sẽ được một thanh tìm kiếm nhìn có vẻ ổn hơn với độ dài được giới hạn là 130px (`outline:none` với mục đích loại bỏ viền màu xanh mặc định của trình duyệt mỗi khi ta nhấp chọn vào thanh tìm kiếm, ta sẽ làm hiệu ứng màu sắc hơn đó một tí sau :3)
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/z3pppvwmmw_Capturdsfe.PNG)
## Tạo hiệu ứng "gậy như ý"
Làm đẹp đã xong, bước tiếp theo ta tiến hành đi đến tạo hiệu ứng cho thanh tìm kiếm mỗi khi nhấp chọn vào. Thứ nhất là **dài ra**. Để khi nhấp chọn vào thanh tìm kiếm nó sẽ dài ra thì ta dùng `:focus` để thiết lập cho nó như sau:
```
input[type="text"]:focus{
	width:500px; 
}
```
Khi nhấp chọn vào thanh tìm kiếm thì độ dài của nó sẽ tăng từ 130px lên 500px (chúng ta có thể làm cho nó dài hơn nếu muốn bằng việc tăng `width` lên)
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/v4a6saum_Capture%20lan%204.PNG)
**Dài ra** đã có, tuy nhiên việc **dài ra** này diễn ra quá nhanh khiến ta không cảm thấy mượt mà và có nét chưa *hiệu ứng* giống "gậy như ý" :v. Cho nên ta sẽ thêm hiệu ứng **từ từ** vào để việc **dài ra** trông mượt mà hơn bằng cách thêm `transition` vào đoạn code CSS ở trên, ta được:
```
	input[type="text"] {
      width: 130px;
      box-sizing: border-box;
      border: 1px solid black;
      border-radius: 4px;
      outline:none;
      padding: 12px 14px;

	  transition:0.6s ease-in-out;
	}
```
Việc thêm transition vào sẽ giúp cho sự **dài ra** của thanh tìm kiếm diễn ra chậm hơn nên sẽ trông mượt mà hơn. Còn 0.6s ở đây là thời gian từ lúc bắt đầu **dài ra** đến lúc đạt được kích cở tuyệt đối mà chúng ta giới hạn, bạn có thể hoàn  toàn tăng thời gian delay lên nếu muốn quá trình diễn ra chậm hơn (chậm ít thôi, chậm nhiều mất hứng lắm :v). Ngoài ra vì việc bỏ đi viền xanh ghi nhấp vào nên ta sẽ trang trí thêm một tí màu để khi nhấp vào trông sẽ đẹp hơn (ở đây mình lọn màu hồng nhạt :3) ta sẽ được đoạn code sau:

```
input[type="text"]:focus{
	width:500px; 
    background-color:lightpink;
}
```
Đây là thanh tìm kiếm của chúng ta sau khi nhấp chọn (trông quá cute :v)
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/3nmiof4c5a_Capture%20lan%205.PNG)
Và dĩ nhiên, hiệu ứng chuyên sang màu hồng cũng sẽ từ từ chuyển sang dựa trên thời gian bạn xét ở `transition`.

Vậy là đã xong việc tạo nên một thanh tìm kiếm với hiệu ứng "gậy như ý" của Tôn Đại Thánh. Chúng ta có thể kết hợp nó vào Navigation Bar để trông hay hơn.

<p data-height="265" data-theme-id="dark" data-slug-hash="Lrvrjw" data-default-tab="css,result" data-user="tortoise10h" data-embed-version="2" data-pen-title="Navigation bar with animated search" class="codepen">See the Pen <a href="https://codepen.io/tortoise10h/pen/Lrvrjw/">Navigation bar with animated search</a>

## Link bài tham khảo
Mình tham khảo tại W3school [ở đây nha](https://www.w3schools.com/css/css_form.asp)


<<<<<Blog-Meta-Data>>>>>
title:Tạo thanh tìm kiếm thò thụt cùng HTML & CSS;publishMode:publish;tags:TIL,html,css;date:2018/08/04 00:00:00;