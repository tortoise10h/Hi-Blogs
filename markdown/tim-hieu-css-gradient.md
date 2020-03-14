Nói đơn giản nhất thì cái **gradients** này kiểu như dùng để chuyển giao hai màu sắc trong cùng một background và khiến người xem cảm thấy rất hòa hợp chứ không đơn thuần là ghép 1 nửa màu này và màu kia lại với nhau.Và trước hết phải lưu ý nếu muốn dùng **gradient** thì chúng ta phải biết rằng bắt buộc dùng 2 màu trở lên cho background (vì một màu thì trải đi đâu).. Đây là ví dụ minh họa cho sự "hòa hợp" đó:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/ixn1az4jts_image.png)
(*hình 1*)
Chứ không kiểu thô thiển như này <i class='em em-laughing'></i>
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/ido0d6by66_image.png)
(*hình 2*)
Sơ lược thì **CSS Gradients** sẽ có hai kiểu là kiểu *trải dài* (`linear-gradient`) và  kiểu vòng tròn :v (`radial-gradient`). (mình dịch ra tiếng Việt khá chuối)
## CSS Linear Gradients
### Các hướng của Linear Gradients
`linear-gradient` là kiểu *trải dài* như hình minh họa ở trên (hình 1). Với `linear-gradient` chúng ta có 4 hướng cơ bản và cách viết trong CSS tương ứng: 
* Từ trên xuống dưới (`linear-gradient(to bottom, color, color,..)`)
* Từ dưới lên trên (`linear-gradient(to top, color, color,..)`)
* Từ trái qua phải (`linear-gradient(to right, color, color,..)`)
* Từ phải qua trái (`linear-gradient(to left, color, color,..)`)
Dưới đây là hình minh họa:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/lmxttzv6w1_image.png)

Ngoài ra chúng ta có thể tùy chỉnh rộng hơn (theo góc độ chúng ta muốn) bằng **angle**. Như việc mình không muốn nó từ trên xuống vuông góc 90 độ như trên mà muốn nó đổ tà tà cở 120 độ thì chỉ cần đơn giản như sau: `linear-gradient(120deg, red ,blue);` (thay chỗ `to bottom` và thay vào đó là độ 'deg là kí hiệu của độ: degrees'). Lưu ý phần góc là góc giữa cạnh đáy (horizontal line) và cạnh của màu bắt đầu (gradient line). Hình minh họa:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/vk6qpo5jo9_image.png)
### Mutiple color stops
Mutiple color stops nôm na là điểm dừng của một màu trong một đống màu mà chúng ta đã cho và từ đó nó sẽ bắt đầu chuyển hóa thành màu khác bằng việc đặt %(tức khoảng muốn kết thúc vào cuối màu đó, như thế này`background: linear-gradient(color %điểm dừng, color %điểm dừng, color %điểm dừng;`). 
Ví dụ:
Đây là 3 màu được cho và với điểm dừng là bằng nhau:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/yafckqpwcu_image.png)
Sau khi ta thay đổi điểm dừng lại một tí như sau `background:linear-gradient(to right,red 60%, yellow 70%, blue 90%);`
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/28h9319gbq_image.png)
Rõ ràng là đã thấy được sự chênh lệch nhẹ :v
### Repeating a linear-gradient
Cách giải thích tốt nhất là xem ví dụ <i class='em em-laughing'></i>
Đây là một **Gradient** bình thường:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/ystqe5dkki_image.png)
Sau khi sử dụng `repeating-linear-gradient`:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/nd1p7faryx_image.png)
Tada!!! (mù mắt <i class='em em-laughing'></i>)
Việc repeat này dựa vào cái **multiple color stops** ở trên, nếu chúng ta cho việc dừng lại của từng màu trong background ở khoảng cách nhỏ thì sẽ tạo thành đoạn nhỏ và nó sẽ còn dư khoảng trống rất nhiều + với `repeating-linear-gradient` sẽ khiến cho các đoạn nhỏ đó lặp lại và ta được kết quả như hình trên. Dĩ nhiên nếu ta cho điểm dừng là quá lớn, như thế này
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/gpi4ytjpky_image.png)
Kết quả:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/gdlrie7v33_image.png)
Thì nó sẽ k lặp lại thành nhiều đoạn nhỏ được. Đáng lẽ ra phải là thế này:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/auv6vzt9mq_image.png)
Và kết quả giống như ban nãy:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/1lij0fekap_image.png)
## CSS Radial Gradients
Phần này thì cũng tương tự như **linear gradient** thay vì trải từ bên này sang bên kia thì nó sẽ là trải từ trung tâm ra ngoài theo "hình tròn".
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/qt3zmjej5w_image.png)
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/nqgnwpmixa_image.png)

Nhưng gì chúng ta biết về `linear-gradient` thì bên `radial-gradient` cũng tương tự, chỉ là khác chút ít.  Như là việc **color stops** ở trên
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/jscztojdqx_image.png)
Kết quả:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/nlk1upgqvj_image.png)

Hay là `repeating`
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/9q2k7zsedo_image.png)
Kết quả:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/pglqy1g4cq_image.png)
(Nhìn ma thuật thế <i class='em em-laughing'></i>)
Chỉ có một thứ khác với `linear-gradient` đó là `radial-gradient` có hai hình dạng đó là `circle` và `ellipse`. (Hình dạng tỏa từ trung tâm theo hình vòng ra ngoài)
* Cirle: sẽ được biểu diễn như sau `background: radial-gradient(circle, red, yellow, green);`
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/sfs3l6janr_image.png)
* Ellipse: `background: radial-gradient( red, yellow, green);` đây là kiểu mặc định nên ta không cần ghi gì thêm
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/exzbyoy4fq_image.png)

Về việc sử dụng các **Gradient** này thì minh hay sử dụng nó làm các background cho phần branding ở header hay một số background cho content trông đẹp hơn. Ví dụ, thay vì bình thường mình hay để branding là một màu (xám chẳng hạn) với cú pháp như này
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/unstkszcu0_image.png)
Thì đây là cái branding của mình:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/rb23h0pi6j_image.png)
Nhưng sau khi thay đổi một tí
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/c2ojwukqfz_image.png)
Nhìn trông cool hơn <i class='em em-laughing'></i>
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/273f4qf2rp_image.png)
Chúng ta hoàn toàn có thể sáng tạo để tạo ra các kiểu background khác trông ngầu và đẹp hơn, có thể là như này :3
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/lnn7tmasvp_image.png)
Code:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/khestihk3y_image.png)
hay ảo diệu như này
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/8x5ssd73xe_image.png)
Code:
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/fl33in7li5_image.png)
## Link tham khảo
Mình tham khảo [Ở đây](https://www.w3schools.com/css/css3_gradients.asp)


<<<<<Blog-Meta-Data>>>>>
title:Tìm hiểu về CSS gradient;publishMode:publish;tags:TIL,css;date:2018/08/25 00:00:00;