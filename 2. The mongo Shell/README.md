
## Database

Lấy thống kê về db
>$ db.stats()

Hiện danh sách các db
>$ show dbs

Hiển thị db hiện tại
>$ db

Chuyển sang db khác, hoặc tạo db mới 
>$ use <database_name>

Xoá db hiện tại, nếu đang không trỏ vào db nào, nó sẽ xoá db mặc định test
>$ db.dropDatabase()


## Collection 

#### Tạo collection 
>$ db.createCollection(name, options)

Các option có thể sử dụng
<table class="table table-bordered">
<tbody><tr><th style="width:15%;">Trường</th><th style="width:15%;">Kiểu</th><th>Miêu tả</th></tr>
<tr><td>capped</td><td>Boolean</td><td>(Tùy ý) Nếu true, kích hoạt một Capped Collection. Đây là một Collection có kích cỡ cố định mà tự động ghi đè các entry cũ nhất khi nó tiếp cận kích cỡ tối đa. <b>Nếu bạn xác định là true, thì bạn cũng cần xác định tham số size</b></td></tr>
<tr><td>autoIndexID</td><td>Boolean</td><td>(Tùy ý) Nếu true, tự động tạo chỉ mục trên các trường _id. Giá trị mặc định là false</td></tr>
<tr><td>size</td><td>Số</td><td>(Tùy ý) Xác định kích cỡ tối đa (giá trị byte) cho một Capped Collection. <b>Nếu tham số capped là true, thì bạn cũng cần xác định trường này</b></td></tr>
<tr><td>max</td><td>Số</td><td>(Tùy ý) Xác định số Document tối đa được cho phép trong một Capped Colleciton</td></tr>
</tbody></table>

Ví dụ tạo collection với các option quan trọng 
>$>db.createCollection("mycollection", { capped : true, autoIndexID : true, size : 6142800, max : 10000 } )

######Collection cũng có thể được thêm tự động khi insert dữ liệu 

#### Xoá collection
>$ db.COLLECTION_NAME.drop()


