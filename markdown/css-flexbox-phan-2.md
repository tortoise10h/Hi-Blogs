Ở phần trước mình đã nói về các property của phần **parent** trong CSS Flex-box (xem lại [ở đây](https://kipalog.com/posts/CSS-Flex-box--Parent--Phan-1)). Hôm nay chúng ta sẽ nói tiếp phần còn lại đó là các property của phần **items**. Trong phần **items** chúng ta sẽ có các property chính sau: **order, flex-grow, flex-shrink, flex-basis, flex và align-self**.
## Các property của items
### order
**order** đơn giản là property dùng để đặt lại thứ tự của các item bên trong parent theo ý của chúng ta, syntax của **order** sẽ là: `order: sốnguyên`. Ví dụ ta có đoạn code sau: 
```
.flex-container{
	display:flex;
	background-color:#ddd;
	flex-wrap:wrap;
}
.child{
	margin:10px;
	padding:10px;
	width:100px;
	font-size:20px;
	background-color:#1abc9c;
}
```
```
<div class="flex-container">
		<div class="child">1</div>
		<div class="child">2</div>
		<div class="child">3</div>
		<div class="child">4</div>
</div>
```
Chúng ta sẽ được như thế này:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/xzxyr229ec_image.png)
Và nếu chúng ta dùng **order** để đặt lại vị trí của các **items** bên trong như sau (chỉ thêm vào, còn lại mọi thứ giữ nguyên) (dùng ngay pseudo-class <i class='em em-laughing'></i>)
```
.child:nth-child(1){order:4;}
.child:nth-child(2){order:1;}
.child:nth-child(3){order:3;}
.child:nth-child(4){order:2;}
```
Thì chúng ta sẽ được như thế này:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/yf6hgak0sv_image.png)
Vị trí của các item bên trong sẽ bị thay đổi theo vị trí mà ta dùng **order** để đặt
###flex-grow
Property này dùng để quy định xem độ lớn của một item sẽ lớn như thế nào so với các item còn lại, syntax của **flex-grow** sẽ là `flex-grow: sốnguyên`. Vẫn với ví dụ ở trên, nếu chúng ta cho 4 item trên đều có flex-grow là 1:
```
.child:nth-child(1){flex-grow:1;}
.child:nth-child(2){flex-grow:1;}
.child:nth-child(3){flex-grow:1;}
.child:nth-child(4){flex-grow:1;}
```
Thì chúng ta sẽ được 4 items bằng nhau như thế này:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/1m3wmju4m0_image.png)
Tuy nhiên nếu chúng ta sửa lại một tí, cho một item có flex-grow là 2 và 3 item còn lại là 1:
```
.child:nth-child(1){flex-grow:1;}
.child:nth-child(2){flex-grow:2;}
.child:nth-child(3){flex-grow:1;}
.child:nth-child(4){flex-grow:1;}
```
Chúng ta sẽ thấy độ lớn của item được xét lên flex-grow 2 sẽ có tỉ lệ gấp đôi các item còn lại:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/n2eg5rwir0_image.png)
### flex-shrink
Nếu như **flex-grow** là quy định độ lớn của item thì **flex-shirnk** sẽ quy định yếu tố co lại của item, nó sẽ quyết định một item sẽ bị co lại như thế nào so với các item còn lại, syntax của nó sẽ là `flex-shrink: sốnguyên`.

Resize browser nhỏ lại thì chúng ta sẽ thấy được item số 1 sẽ bị co lại nhỏ hơn so với 3 item kia tại vì nó được chỉnh `flex-shrink:6`:
<p data-height="265" data-theme-id="dark" data-slug-hash="ZjvGdo" data-default-tab="css,result" data-user="tortoise10h" data-pen-title="flex-shrink example1" class="codepen"> <a href="https://codepen.io/tortoise10h/pen/ZjvGdo/">flex-shrink example1</a> 
### flex-basis
**flex-basis** dùng để quy định độ dài ban đầu của một item, syntax của nó: `flex-basis: đơnvịđộdài`. Nếu ta có class child và độ dài của nó là 100px và chúng ta tùy chỉnh item thứ 2 trong 4 item với `flex-basis:300px`thì ta sẽ được như sau:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/nwblromqa2_image.png)
### flex
**flex** là property dùng để ghi tắc cho 3 property ở trên: **flex-grow, flex-shrink và flex-basis**. thay vì chúng ta phải ghi:
```
.child{
  flex-grow:1;
  flex-shrink:6;
  flex-basis:300px;
}
```
thì ta sẽ có thể ghi gọn hơn với **flex**: `flex:1 6 300px;`. Và lưu ý:
* Nếu ta dùng flex và  viết chỉ với một số  thế này: `flex:1;` thì nó sẽ hiểu đó chính là **flex-grow**.
* Nếu ta dùng flex và viết với một "đơn vị độ dài" như thế này: `flex:200px;` thì nó sẽ hiểu là **flex-basis**.
* Nếu ta dùng flex và viết với hai giá trị như thế này: `flex:1 200px;` thì nó sẽ hiểu là **flex-grow** và **flex-basis**
*  Nếu ta dùng flex và viết với hai giá trị như thế này: `flex:1 2;` thì nó sẽ hiểu là **flex-grow** và **flex-shrink**
*  Và nếu ta dùng flex và viết với 3 giá trị như thế này `flex;1 2 300px` thì sẽ lần lượt là **flex-grow, flex-shrink** và **flex-basis**.

### align-self
Property này có công dụng cũng giống như **align-items** của phần **parent** tuy nhiên nó là dùng phần **items**, chúng ta có thể dùng nó để đặt lại vị trí cho một số item ta thích (hoặc tất cả) mà **align-items** đã quy định, **align-self** cũng có các giá trị giống như là **align-items** đó là: **flex-start, flex-end, center, stretch và baseline**. Ví dụ ta có 8 item đã được căn ra giữa nhờ `align-items:center` như sau:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/7u4ljzeqvg_image.png)
Tuy nhiên ta lại muốn thằng thứ 3 là phải nằm ở dưới cùng, thằng thứ 5 thì phải kéo giãn dài ra và thằng thứ 7 thì phải nằm trên đầu thì ta chỉ việc dùng **align-self** để đặt lại cho nó.
```
.child:nth-child(3){align-self:flex-end;}
.child:nth-child(5){align-self:stretch;}
.child:nth-child(7){align-self:flex-start;}
```
Và đây là kết quả:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/p8wviekasn_image.png)

## Link tham khảo
* W3School [ở đây](https://www.w3schools.com/css/css3_flexbox.asp)
* CSS0-tricks [ở đây](https://css-tricks.com/almanac/properties/a/align-self/) (đây là phần align-selft kéo xuống sẽ thấy related với các property khác)


<<<<<Blog-Meta-Data>>>>>
title:CSS Flexbox phần 2: Items;publishMode:publish;tags:TIL,css;date:2018/09/08 00:00:00;