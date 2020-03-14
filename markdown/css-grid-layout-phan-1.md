Như lần trước ,mình đã nói về [Flex-box layout module](https://kipalog.com/posts/CSS-Flex-box--Parent--Phan-1) thì lần này chúng ta sẽ tiếp tục với một layout module mới, đó chính là **Grid layout module** - một layout module khác của CSS. **Grid layout module** (aka **grid**), khác với Flex-box ta đã nói ở phần trước, Flex-box là layout module một chiều - tức là một là hàng hai là cột chứ không thể cả hai, thì khi làm việc với **Grid** nó sẽ làm được điều đó, **grid** chia layout của một trang web ra cho chúng ta thao tác cả hàng lẫn cột.
Grid rows:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/zveqtq2tmj_image.png)
Grid colums:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/e5qcnenyqx_image.png)
Và **Grid**  cũng tương tự như **Flex-box** ở chỗ là cấu trúc cũng được chia ra làm hai phần, đó là phần **parent** (hay là **container**)  và phần **items** bên trong. Ở phần container chúng ta cần phải có `display:grid` (giống như là bên **flex-box** thì sẽ là `display:flex`).
```
.container{
	display;grid | inline-grid
}
```
Ở đây chúng ta có cả `grid` và `inline-grid`, hai cái này thì về các property sử dụng là như nhau chỉ khác nhau ở chỗ là:
* `grid`: tạo ra layout có level là block
* `inline-grid`: tạo layout có level là inline

Trong bài này chúng ta sẽ đi đến với các property chính ở phần **container** (bài sau sẽ là phần **items** )
## Các propery của container
### grid-template-columns/rows
Đầu tiên chúng ta sẽ nói về hai propery quan trong này trước đó là: `grid-template-columns` và `grid-template-rows`. Chúng ta sẽ cho một ví dụ mẫu, ta có một đoạn `html` như này:
```
<div class="grid-container">
        <div>1</div>
        <div>2</div>
        <div>3</div>
        <div>4</div>
        <div>5</div>
        <div>6</div>
        <div>7</div>
        <div>8</div>
 </div>
```
Và đương nhiên ở phần CSS cho `grid-container` phải nhớ có `display:grid`
```
.grid-container{
        display:grid;
        background-color:#eaeaea;
        padding:1em;
    }
    .grid-container > div{
        background:#1abc9c;
        padding:1em;
    }
```
Và đương nhiên nếu chỉ có như vậy thì chúng ta vẫn chưa thấy được gì cả:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/gsqm8kgil4_image.png)
Cho nên chúng ta sẽ cần tới hai property ở trên để tạo ra layout khi sử dụng **grid**.
#### grid-template-columns
Property này có tác dùng là giúp chúng ta quyết định trong **container** của chúng ta có bao nhiêu cột:
```
.grid-container{
        display:grid;
        grid-template-columns:đơnvị đơnvị đơnvị .....;
    }
```
Phần đơn vị ở trên chúng ta có thể dùng các đơn vị độ dài:px, em, cm,.. hay % hoặc là phân số (kí hiệu là `fr`, tìm hiểu rõ về `fr` [tại đây](https://alligator.io/css/css-grid-layout-fr-unit/)) để quyết định độ rộng của mỗi cột. Ví dụ ta muốn biến ví dụ trên thành mỗi hàng sẽ có 3 cột ta sẽ làm như sau:
```
.grid-container{
        *đống code cũ*
        grid-template-columns:1fr 1fr 1fr;
    }
```
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/c50i8rdj3r_image.png)
Chúng ta đã được 3 cột trên một hàng, tương tự nếu như muốn là 4 cột thì chỉ cần ghi `grid-template-columns:1fr 1fr 1fr 1fr;` và nhiều hơn nữa.

Chúng còn một cách chia layout nữa, đó là dùng hàm `repeat()`, nếu chúng ta muốn chia layout ra làm 3 phần như ở trên bằng `repeat()` thì ta có thể viết như sau:
```
.grid-container{
        /*đống code cũ*/
        grid-template-columns:repeat(3, 1fr);
    }
```
Chúng ta sẽ được kết quả tương tự. Với số 3 sẽ tượng trưng cho số lần lặp lại và đơn vị sau dấu phẩy sẽ là độ rộng của mỗi cột, ta có thể thêm nhiều hơn 1 đơn vị sau dấu phẩy, ví dụ như thế này `grid-template-columns:repeat(3, 1fr 3fr);` Thì kết quả sẽ là một cột 1fr một cột 3fr lặp lại 3 lần:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/6h9k2au2bz_image.png)
#### grid-template-rows
Property này sẽ tác dụng lên dòng, nó sẽ quy định độ cao của mỗi dòng là như thế nào
```
.grid-container{
        display:grid;
        grid-template-rows:đơnvị đơnvị đơnvị .....;
    }
```
ví dụ ta có:
```
.grid-container{
        display:grid;
      	grid-template-columns:repeat(3, 1fr);
        grid-template-rows:100px 200px;
    }
```
Thì ra sẽ được:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/yelociv38h_image.png)
hàng thứ 3 chúng ta không viết nên nó sẽ là mặc định
### Grid-gap:
Như chúng ta biết ở trên Grid layout module sẽ chia ra cột và dòng, giữa cột và dòng đó chúng ta sẽ có các đường ngắn cách như thế này:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/7cm99neik0_image.png)
**grid-gap** chính là property dùng để thao tác lên các đường ngắn cách đó, cụ thể là nếu xét **grid-gap** càng lớn thì độ rộng của các đường thằng đó cũng càng lớn.

**grid-gap** chính là phần viết tắc cho hai property **grid-column-gap** (thao tác cho các đường ngăn cách trên cột) và **grid-row-gap** (thao tác cho các đường ngăn cách trên dòng)
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/7oylyhen5u_image.png)
Bình thường nếu chúng ta chia layout trong grid mà không có margin (cho phần items) hay grid-gap thì nó sẽ được như thế này:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/pmeo8qhjec_image.png)
Và và nếu ta thêm vào `grid-column-gap:1em;`
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/5jmwz3y34c_image.png)
Thêm vào `grid-row-gap:2em;`
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/pt2ssngwvo_image.png)
Và có thể thay thế hai dòng trên bằng `grid-gap:1em 2em`
### justify-items
Property này dùng để căn chỉnh các **items** bên trong **container** theo trục đứng dựa trên vị trí hàng và cột của nó. Lấy lại ví dụ ở trên:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/ulsau8omjq_image.png)
Ta sẽ đi đến với các giá trị của **justify-items**:
* **justify-items:start** giá trị này giúp căn các **items** bên trong về đầu trục (trục đứng). Nếu ta dùng `justify-items:start` lên hình ví dụ thì ta sẽ được: ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/ywiyyn0t7m_image.png) Các **items** bên trong đã được kéo về đầu trục và đồng thời cũng trở về đúng với chiều rộng của nó  (không bị kéo giãn ra cho full màn hình nữa). Và chúng ta đã nói ở trên trong **grid** các items chia ra theo từng hàng và cột và có các đường ở giữa (các đường thẳng đã nói ở phần **grid-gap**) nên sau khi bị căn chỉnh các items sẽ được đưa về tới đầu trục thẳng đó (nên ta mới thấy có các khoảng cách giữa các items)
* **justitfy-items:end** ngược lại với **start** ở trên thì chúng ta sẽ có **end**, giá trị này sẽ căn các items bên trong về cuối trục đứng:![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/i60t0z8hmh_image.png)
* **justify-items:center** cái này thì sẽ căn các items ra giữa trục: ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/lfv3uivnel_image.png)
* **justify-items:stretch** đây là giá trị mặc định, nó sẽ giãn items bên trong dài ra cho vưà hết màn hình (như hình ví dụ ban đầu)


### align-items
Ngược lại với **justify-items** (thao tác dựa trên trục đứng) thì **align-items** sẽ là thao tác trên trục ngang, các giá trị có tác dụng tương tự như của **justify-content** nhưng với trục ngang. Chúng ta sẽ có một hình mới với chiều cao được cho là 500px:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/6a6c42kq6d_image.png)
* **align-items:start**: ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/yfv24cwbaz_image.png)
* **align-items:end** ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/4ol236gka3_image.png)
* **align-items:center**![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/icz82bgzw1_image.png)
* **align-items:stretch** Và stretch chính là giá trị mặc định ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/6a6c42kq6d_image.png)

### justify-content
Cũng giống như **justify-items** đó là thao tác căn chỉnh các items trên trục đứng, tuy nhiên nếu như **justify-items** là căn chỉnh cho các items dựa trên các đường thẳng phần chia hàng và cột thì **justify-content** sẽ là căn chỉnh nguyên cả khối items. Chúng ta sẽ chỉnh lại một tí với `grid-template-columns:50px 50px 50px;` để các items giảm chiều rộng lại thì ta mới thấy được cách **justify-content** vận hành. ta có ví dụ:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/2y82o0ndec_image.png)
Các items đã được giảm chiều rộng xuống còn 50px:
* **justify-content:end** khối items sẽ được đưa về cuối contianer:![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/ioi0ons3a8_image.png)
* **justify-content:center** khối items sẽ được đưa ra giữa container: ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/7av42l97t5_image.png)
*  **justify-content:start** khối items được đưa về đầu container: ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/2y82o0ndec_image.png)
*  **justify-content:space-around**: bọc các khoảng trống bằng nhau xung quanh mỗi items theo trục đứng: ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/ucmbla7gai_image.png)
*  **justify-content:space-evenly**: cũng là bọc khoảng trống xung quanh các items, tuy nhiên các khoảng trống này là bằng nhau  (xem hình ở **space-evenly** và **space-around** để so sánh): ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/orwfbll2qn_image.png)
*  **justify-content:space-between**: cũng là bọc các khoảng trống đều nhau xung quanh items tuy nhiên sẽ không có ở điểm đầu và cuối: ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/4a9frs2v91_image.png)


### align-content
Nếu như **align-items** là ngược lại của **justify-items** còn lại thì tính chất của các giá trị hoàn toàn giống nhau (chỉ khác là **justify-items** là tục đứng còn **align-items** là trục ngang) thì **align-content** cũng y chang như vậy. Chúng ta sẽ lấy hình mẫu của **align-items** để minh họa:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/6a6c42kq6d_image.png)
* **align-content:end**![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/xu9ks46hj2_image.png)
* **align-content:center**![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/70elgb8alj_image.png)
* **align-content:start**![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/hyqxiucn15_image.png)
* **align-content:space-around**![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/lvgj49ueeo_image.png)
* **align-content:space-evenly**![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/w1ehihqj2y_image.png)
* **align-content:space-between**![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/cpiqyz8m62_image.png)
* **align-content:stretch** là giá trị mặc định sẽ kéo giãn các items ra, như hình ví dụ đầu

## Link tham khảo
* W3School [ở đây](https://www.w3schools.com/css/css_grid_container.asp)
* CSS-tricks [ở đây](https://css-tricks.com/snippets/css/complete-guide-grid/)

<<<<<Blog-Meta-Data>>>>>
title:CSS grid layout model phần 1;publishMode:publish;tags:TIL,css;date:2018/09/10 00:00:00;