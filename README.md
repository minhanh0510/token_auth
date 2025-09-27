npm install
-Khởi chạy server App : node app.js

Đăng ký thành công
Method: POST
URL: http://localhost:3000/api/auth/register
Body (raw JSON): 
{
  "username": "minhanh",
  "email": "minhanh@email.com",
  "password": "123456"
}

Kết quả: "User registered successfully!"
![alt text](public/image/1.png)
Check in Database
![alt text](public/image/2.png)

==================================================
Đăng ký không thành công
Method: POST
URL: http://localhost:3000/api/auth/register
Body (raw JSON): 
{
  "username": "minhanh",
  "email": "minhanh@email.com",
  "password": "123456"
}

Kết quả: 
{
    "error": "E11000 duplicate key error collection: tokenAuthApp.users index: username_1 dup key: { username: \"minhanh\" }"
}
![alt text](public/image/3.png)

==================================================
Đăng nhập để lấy token
Method: POST
URL: http://localhost:3000/api/auth/login
Body (raw JSON): 
{
  "email": "minhanh@email.com",
  "password": "123456"
}
Kết quả:
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjY4ZDc1MTI2OTE0OGYyOTMzNDY3ZDJiZCIsImlhdCI6MTc1ODk0MTg5NiwiZXhwIjoxNzU4OTQ1NDk2fQ.ZdKBmDQ6Y2niA9780Gacr7x6aM34SvBOGCq4FCcEbLY"
}
![alt text](public/image/4.png)

==================================================
Truy cập Profile (có token)
Method: GET
URL: http://localhost:3000/api/auth/profile
Authorization: Bearer Token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjY4ZDc1MTI2OTE0OGYyOTMzNDY3ZDJiZCIsImlhdCI6MTc1ODk0MTg5NiwiZXhwIjoxNzU4OTQ1NDk2fQ.ZdKBmDQ6Y2niA9780Gacr7x6aM34SvBOGCq4FCcEbLY
Kết quả:
{
    "_id": "68d751269148f2933467d2bd",
    "username": "minhanh",
    "email": "minhanh@email.com",
    "__v": 0
}
![alt text](public/image/5.png)

==================================================
Truy cập Profile (không token)
Method: GET
URL: http://localhost:3000/api/auth/profile
Kết quả: "error": "Access denied"
![alt text](public/image/6.png)

==================================================
Giảm tg sống của token

const token = jwt.sign({ id: user._id }, 'secretKey', { expiresIn: '60s' });

![alt text](public/image/7.png)

==================================================
Truy cập Profile (có token) nhưng hết th
Method: GET
URL: http://localhost:3000/api/auth/profile
Kết quả: "error": "Invalid token"
![alt text](public/image/8.png)
![alt text](public/image/9.png)
![alt text](public/image/10.png)

