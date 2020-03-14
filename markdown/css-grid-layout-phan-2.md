Ở bài trước chúng ta đã tìm hiểu về [các property của container trong css grid layout module](https://kipalog.com/posts/CSS-grid-layout-model--Container--Phan-1). Thì tiếp theo phần 1, bài này chúng ta sẽ tìm hiểu nốt phần còn lại đó chính là **các property chính của phần items**.
## Các property của items
### grid-column / grid-row
Như chúng ta đã biết ở bài trước, trong **grid** các items được chia theo hàng và cột,  và ở giữa mỗi hàng và cột thì chúng ta sẽ có những đường như thế này:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/m12ykhlryc_image.png)
(*Nguồn w3school*)
Khi sử dụng **grid-column** hay **grid-row** là chúng ta sẽ phải dùng đến những đường thẳng này.
#### grid-column
**grid-column** này là cách viết tắc cho **grid-column-start** và **grid-column-end** và công dụng của **grid-column-start** và **grid-column-end** như thế nào thì chúng ta sẽ đi đến ví dụ sau, đây là một **container** với các **items** bên trong như thường lệ (và trong hình dưới mình sẽ đánh số cho các đường thẳng ở dòng và cột để tiện giải thích):
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/t30d3o824j_image.png)
Nếu ta thêm vào items số 1 như sau:
```
/*chúng ta dùng pseudo class để chọn div số 1 - tức item số 1*/
.grid-container > div:nth-child(1){
        grid-column-start:1;
        grid-column-end:3;
    }
```
Ta sẽ có kết quả như sau:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/7wf0vo9ggj_image.png)
Như chúng ta đã thấy, sau khi sử dụng `grid-column-start:1;` và `grid-column-end:3;` thì chiều rộng của items 1 đã trở nên gấp đôi các items khác, nói đúng nhất là bình thường chiều rộng của items 1 sẽ từ **line 1c** cho tới **line 2c** như hình ban đầu (**line 1c**, **line 2c** là mình dùng để ám chỉ các đường thẳng của cột) sau khi sử dụng `grid-column-start:1;` và `grid-column-end:3;` có nghĩa là ta sẽ quy định lại item 1 sẽ có chiều rộng từ **line 1c** đến tận **line 3c** cho nên ta thấy nó sẽ kéo dài ra bằng hai item bình thường. Ta sẽ tiếp tục thực hiện lên một item khác, ta sẽ chọn item 12
```
.grid-container > div:nth-child(12){
        grid-column-start:1;
        grid-column-end:5;
    }
```
Lần này ta sẽ cho chiều dài của item 12 kéo dài từ **line 1c** cho đến **line 5c**, ta được kết quả như sau:
	![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/afehpoz1hg_image.png)
 Và ta có thể sử dụng cách viết tắc **grid-column** thay thế cho cả 2 **grid-column-start** và **grid-column-end**, ví dụ ta dùng grid-column cho đoạn CSS của item 1 ở trên thì sẽ là:
 ```
 .grid-container > div:nth-child(1){
        grid-column:1 / 3;
    }
 ```
 chúng ta sẽ được kết quả tương tự ở trên. syntax của **grid-column** là: 
 ```
 grid-column: đườngbắtđầu /  đườngkếtthúc
 ```
 Ngoài ra nếu thay vì ta viết `grid-column:1 / 3` thì ta có thể viết `grid-column: 1 / span 2`. Ở cách viết trên  số `1` vẫn là đánh dấu cho điểm bắt đầu, tuy nhiên `span 2` ở đây có nghĩa là nó sẽ kéo từ **line 1c** và vượt qua **line 2c** cho đến khi chạm tới đầu **line 3c** thì hết. Ta sẽ thử lên item 4 như sau
 ```
 .grid-container > div:nth-child(4){
        grid-column:1 / span 3;
    }
 ```
 Kết quả:
 ![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/6j8dmvm6bb_image.png)
 Chúng ta thấy item 4 kéo dài từ **line 1c** và chạm đến **line 4c** các viết đó cũng giống như viết thế này:
 ```
 .grid-container > div:nth-child(4){
        grid-column:1 / 4;
    }
 ```
#### grid-row
Ngược lại với **grid-column** thì chúng ta có **grid-row**, cách thức hoạt động của **grid-row** thì cũng giống **grid-column** nhưng thay vì là các đường thẳng ở cột thì **grid-row** sẽ là nhưng đường hẳng ở hàng. Và đương nhiên **grid-row** là các viết tắc cho **grid-row-start** và **grid-row-end**. Lấy lại hình ví dụ ở trên để ta thực hiện ví dụ với **grid-row**
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/t30d3o824j_image.png)
Ví dụ ta chọn item số 1 để thực hiện cách viết thông thường với **grid-row-start** và **grid-row-end**:
```
.grid-container > div:nth-child(1){
	grid-row-start:1;
    grid-row-end:4;
}
```
Ta sẽ được:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/3qvfu2oz98_image.png)
Sử dụng **grid-row** lên item 8 xem:
```
.grid-container > div:nth-child(8){
	grid-row:3 / 5;
}
```
Kết quả:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/k5uws8vu39_image.png)
Cuối cùng là dử dụng `span`:
```
  .grid-container > div:nth-child(2){
      grid-row:1 / span 2;
  }
```
Kết quả:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/7dty4h0dv_image.png)
### justify-self
Ở bài trước chúng ta đã tìm hiểu về **justify-items** là có tác dụng căn chỉnh các items bên trong nào là về đầu trục, cuối trục, ra giữa hay kéo giãn. Thì với **justify-self**, nó tạo ra với tác dụng là làm trái lệnh từ **justify-items** vậy. Ví dụ ta có hình như sau:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/h0yvyd8797_image.png)
và nếu ta sử dụng `justify-items:center` ở **container** thì tất cả các items sẽ được căn hết vào giữa như thế này:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/l3u72uv5m2_image.png)
Tuy nhiên ví dụ thằng số 7 muốn phá luật, nó muốn kéo giãn ra chứ không muốn bị co lại và căn ra giữa nữa, thì ta làm như sau:
```
 .grid-container > div:nth-child(7){
        justify-self:stretch;
    }
```
Boom:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/9e3ikqzzdh_image.png)
Thằng số 7 lách luật thành công. các giá trị của **justify-self** cũng tương tự như justify-items như: **end, start, center** và **stretch** nhưng nó chỉ tác dụng lên được item được chỉ định như cái tên của nó - **self** chứ không tác dụng lên toàn bộ item.
### align-self
Nếu như **justify-self** là dùng để lách luật của **justify-items** thì **align-items** cũng có thằng lách luật của nó, đó chính là **align-self**. Cũng giống như **justify-self** thì **align-self** cũng *chỉ tác dụng lên được item được chỉ định như cái tên của nó - self chứ không tác dụng lên toàn bộ item.* Và nó cũng có các giá trị tương tự: **end, start, center** và **stretch**. Điều duy nhất khác với **justify-self** đó chính là **justify-self** tác dụng lên cột còn **align-self** sẽ tác dụng lên hàng.
**align-items** ban hành luật `align-items:center`:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/vbrf1418a4_image.png)
và **align-self** lách luật với
```
.grid-container > div:nth-child(6){
        align-self:start;
    }
```
Kết quả:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/i8actdncjz_image.png)
## link tham khảo
* [W3School](https://www.w3schools.com/css/css_grid_item.asp)
* [CSS-tricks](https://css-tricks.com/snippets/css/complete-guide-grid/)


<<<<<Blog-Meta-Data>>>>>
title:CSS grid layout model phần 2;publishMode:publish;tags:TIL,css;date:2018/09/15 00:00:00;