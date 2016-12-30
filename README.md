## Kiểu dữ liệu trong MongoDB


- Chuỗi: Chuỗi trong MongoDB phải là UTF-8 hợp lệ.
- Số nguyên: Số nguyên có thể là 32 bit hoặc 64 bit phụ thuộc vào Server.
- Boolean: lưu trữ giá bị boolean true/false.
- Double: Lưu các giá trị số thực dấu chấm động.
- Min/Max keys: Sử dụng để so sánh một giá trị với các phần tử BSON thấp nhất và cao nhất.
- Mảng: Lưu trữ các mảng, hoặc danh sách, hoặc nhiều giá trị vào trong một key.
- Timestamp: Ghi chép hoặc đánh dấu thời điểm một Document được sửa đổi hoặc được thêm vào.
- Object: Sử dụng cho các Document được nhúng vào.
- Null: Lưu một giá trị null.
- Symbol: Sử dụng giống như một chuỗi, tuy nhiên , nói chung nó được dành riêng cho các ngôn ngữ mà sử dụng kiểu symbol cụ thể.
- Date: Sử dụng để lưu trữ date và time hiện tại trong định dạng UNIX time. Có thể xác định date time riêng bằng việc tạo đối tượng Date và truyền ngày, tháng, năm vào trong đó.
- Object ID: Để lưu trữ ID của Document.
- Binary data: Sử dụng để lưu trữ dữ liệu nhị phân.
- Code: Lưu trữ JavaScript code vào trong Document.
- Regular expression: Để lưu trữ Regular Expression.


## Document 

### INSERT
Sử dụng phương thức ```insert()``` 
>$ db.COLLECTION_NAME.insert(document)

>Note:
 - document có thể là một object JSON hoặc một mảng JSON.
 - _id: ObjectId(7df78ad8902c): _id là một số thập lục phân duy nhất, dài 12byte. 

Sử dụng phương thức ```save()```
>$ db.COLLECTION_NAME.insert(document)

>Note:
 - Nếu không xác định ```_id```: thì phương thức save() sẽ làm việc giống như phương thức insert().
 - Nếu bạn xác định ```_id```: thì sẽ là <b>UPDATE</b> toàn bộ dữ liệu của document chứa ```_id``` đó.


### SELECT

- Phương thức <b>find()</b>
: Hiển thị tất cả Document ở dạng không có cấu trúc.
>$ db.COLLECTION_NAME.find()

 - Projection: chỉ chọn dữ liệu cần lấy thay vì toàn bộ dữ liệu của document.
 >$ db.collection.find({}, {KEYA:1, KEYB:0})
 - Key là 1 thì sẽ được hiện ra, 0 để ẩn. 


- Phương thức <b>pretty()</b>
: Để hiển thị các kết quả theo một cách đã được định dạng 
>$ db.mycol.find().pretty()

Ngoài phương thức ```find()```, phương thức ```findOne()``` sẽ chỉ trả về một Document.

#### Truy vấn theo điều kiện

<table class="table table-bordered">
<tbody><tr><th>Phép toán</th><th>Cú pháp</th><th>Ví dụ</th><th style="width:35%;">Mệnh đề WHERE tương đương</th></tr>
<tr><td>Equality</td><td>{&lt;key&gt;:&lt;value&gt;}</td><td>db.mycol.find({"by":"tutorials point"}).pretty()</td><td>where by = 'tutorials point'</td></tr>
<tr><td>Less Than</td><td>{&lt;key&gt;:{$lt:&lt;value&gt;}}</td><td>db.mycol.find({"likes":{$lt:50}}).pretty()</td><td>where likes &lt; 50</td></tr>
<tr><td style="width:35%;">Less Than Equals</td><td>{&lt;key&gt;:{$lte:&lt;value&gt;}}</td><td>db.mycol.find({"likes":{$lte:50}}).pretty()</td><td>where likes &lt;= 50</td></tr>
<tr><td>Greater Than</td><td>{&lt;key&gt;:{$gt:&lt;value&gt;}}</td><td>db.mycol.find({"likes":{$gt:50}}).pretty()</td><td>where likes &gt; 50</td></tr>
<tr><td>Greater Than Equals</td><td>{&lt;key&gt;:{$gte:&lt;value&gt;}}</td><td>db.mycol.find({"likes":{$gte:50}}).pretty()</td><td>where likes &gt;= 50</td></tr>
<tr><td>Not Equals</td><td>{&lt;key&gt;:{$ne:&lt;value&gt;}}</td><td>db.mycol.find({"likes":{$ne:50}}).pretty()</td><td>where likes != 50</td></tr>
</tbody></table>

#### AND
Trong phương thức ```find()``` nếu truyền nhiều key bằng cách phân biệt chúng bởi dấu phẩy,
 thì MongoDB xem nó như là điều kiện <b>AND</b>:
>$ db.collectionname.find({key1:value1, key2:value2}).pretty()


#### OR
Cần sử dụng từ khoá $or 
>$ db.collectionname.find({ $or:[{"by":"tutorial spoint"}, {"title":"MongoDB Overview"}] }).pretty()

Ví dụ trên sẽ hiển thị tất cả bản ghi trong collection: collectionname được viết bởi 'tutorial spoint' hoặc có title là 'MongoDB Overview'


#### AND và OR

>$ db.collectionname.find({ "likes":{$gt:10}, $or:[{"by":"spoint", {"title":"MongoDB"} }] }).pretty()

tương đương với truy vấn SQL là: ```'where likes>10 AND (by = 'point' OR title = 'MongoDB')'```



### UPDATE

MongoDB cung cấp các phương thức để update các bản ghi trong 1 collection:

- db.collection.updateOne()
- db.collection.updateMany()
- db.collection.replaceOne()
- db.collection.update()

Các phương thức sau cũng có thể update được:
- db.collection.findOneAndReplace()
- db.collection.findOneAndUpdate()
- db.collection.findAndModify()
- db.collection.save()
- db.collection.bulkWrite()


### DELETE 

- db.collection.remove()
- db.collection.deleteOne()
- db.collection.deleteMany()

- db.collection.findOneAndDelete()
- db.collection.findOneAndModify()
- db.collection.bulkWrite()

Phương thức ```remove()``` có thể truyền như sau 
>$ db.collection.remove(DELLETION_CRITTERIA, JUST_ONE)
- DELLETION_CRITTERIA: (tuỳ chọn) xác định Document để xoá
- JUST_ONE: (tuỳ chọn) nếu là true hoặc 1, thì chỉ xoá 1 Document.
- nếu không truyền gì vào thì sẽ xoá tất cả các documents trong collection đó.


### LIMIT 
Giới hạn bản ghi lấy ra
>$ db.collection.find().limit(NUMBER)

### SKIP 
Nhảy qua 10 bản ghi và lấy ra 20 bản ghi. Giá trị mặc định trong phương thức ```skip()``` là 0
>$ db.collection.find({}, {"title":1, _id:0}).limit(20).skip(10)


### SORT
1: tăng dần, -1: giảm dần. Câu lệnh sau sắp xếp các bản ghi theo title tăng dần. 
Nếu không xác định thứ tự sắp xếp thì phương thức ```sort()``` sẽ hiển thị document theo thứ tự tăng dần. 
>$ db.collection.find().sort({"title":1}) 






