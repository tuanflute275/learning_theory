## cấu hình cấu trúc node nhanh
**step by step**
1. npm install -g express-generator
2. express --view=ejs ten_folder
3. npm install 
4. npm start 
> http://localhost:3000

## câu lệnh npm
    npm init 
>(tạo file package.json)

## cài đặt express
1.   npm install --save-exact express@4.17.1
2. import Express from "express";
3. const app = express(); và app.method(path, handle)

## cài node mon
1.  npm i nodemon
2. vào file ***package.json*** thêm câu lệnh vào **scripts**

     `"start": "nodemon --exec babel-node src/server.js"`

## cài morgan 
- nó giúp ta biet phuong yhuc nao minh gui di va mot so thong tin khac

        npm i morgan
        var morgan = require('morgan')
        app.use(morgan('combined'))
    
> file .gitignore dùng để ẩn nội dung khi đẩy lên github --> .gitignore

## VIEW ENGINE (handlebar)
- dùng để hiển thị ra giao diện wed

**step1**

    npm install express-handlebars
    npm i ejs

**step2**

    import path from 'path'
    
**step3**

    muốn sử dụng ta cần có đoạn code sau ở file server.js
    // setting ejs
        app.set("view engine", "ejs");
        app.set('views', path.join(__dirname, 'resources/views'))

    -- nó sẽ sử dụng view engine là ejs
    -- path _dirname là để build ra từ file nào

## config viewEjs
    import express from "express";
    const configViewEngine = (app) => {
        app.use(express.static('./src/public'))
        // cấu hình view engine là ejs
        app.set("view engine", "ejs");
        app.set("views", "./src/resources/views")
    }

    export default configViewEngine;

## sass - nodejs
**install**

    npm i node-sass

**cấu hình**

>vào file package.json để config

>thêm câu lệnh sau vào phần **script** như start

`"watch": "node-sass --watch src/resources/scss/app.scss src/public/css/app.css",`

***chạy câu lệnh npm run watch ở terminal khác***

    npm run watch


## cài đặt babel nó hỗ trợ các câu lệnh mới nhất ( import)
**setp1**

    npm install --save-exact body-parser@1.19.0 nodemon@2.0.12 @babel/core@7.15.5 @babel/node@7.15.4 @babel/preset-env@7.15.6

**step2**

>tạo file .babelrc  để config babel

`{
    "presets": [
        "@babel/preset-env"
    ]
}`

## STATIC FILES
    // static file
    app.use(express.static(path.join(__dirname, 'public')))
>public là thư mục muốn static

## tạo cổng từ file khác
- tạo file .env để lưu cổng web  (ví dụ PORT = 8080)
- và nodeJs muốn dùng phải cài đặt dotenv
    
        npm install --save-exact dotenv@10.0.0
    
    **muốn sử dụng cần cấu hình**

         require('dotenv').config();
    vào file **server.js** và

        const port = process.env.PORT
    

## mô hình mvc
action --> dispatcher --> function handler

    app.get('/news', (req, res) => {
        res.render('news.ejs');
    });

> app.get('/news',... )  --> đây đc gọi là routes --> viết ở file khác


**controller**

- app.get('/news',handle() )  --> function handle trong đây dc gọi là controller và nó dc viết ở file khác 

- controller tương tác với view ở chỗ nó render ra file html-css trong thư mục view

- cum này (req, res) => {
    res.render('news.ejs');
} được viết ở file controller sẽ đúng mô hình mvc


**module**

- SỬ DỤNG DATABASE VỚI NODE.JS

        npm i --save-exact mysql2@2.3
        npm i mysql2

> tạo file connectDB.js 
và thêm code này rồi export ra file homeController trong thư mục controller(homecontroller sẽ import)


**connectDB export file ra homeController**

    const connection = mysql.createConnection({
        host: 'localhost',
        user: 'root',
        database: 'nodebasic'
    });

    export default connection;

***homeController import file vào và thêm câu lệnh trong mỗi layout muốn lấy database***

    import connection from '../config/connectDB'
    exports.home = function (req, res) {
        // lấy database
        let data = [];
        connection.query(
            'SELECT * FROM `users` ',
            function (err, results, fields) {
                results.map((row) => {
                    data.push({
                        id: row.id,
                        email: row.email,
                        address: row.address,
                        name: row.name
                    })
                })
                return res.render('index.ejs', { dataUser: JSON.stringify(data) });
            }
        );
    }

***render database ra view ejs cho browser(web, chrome, firefox,...) nhìn thấy***

- trong file index.ejs để có thể nhìn thấy ta thêm dataUser của file homecontroller vào
- bằng cách sau: <%= dataUser %>


## tạo orm với mysql
👉 1. Cài đặt các thư viện: sequlize-cli, sequelize và mysql2
npm install --save-dev sequelize-cli@6.2.0
npm install --save mysql2@2.2.5
npm install --save sequelize@6.6.2

👉 2. Tại thư mục root, sử dụng câu lệnh: node_modules/.bin/sequelize init

👉 3. Tạo model: 
npx sequelize-cli model:generate --name User --attributes firstName:string,lastName:string,email:string

👉 4. Tạo migrations:
npx sequelize-cli db:migrate
----- lỗi : vào file .env thêm câu NODE_ENV=development này vào

👉 5. Tạo Seeder: npx sequelize-cli seed:generate --name demo-user

>dán câu lệnh config vào: npx sequelize-cli init -->thay = câu node modules ở trên r
>khi chạy nh câu lệnh trên nó sẽ lỗi

### và ta cần tạo 1 file để config là **.sequelizerc**
----
    const path = require('path');
    module.exports = {
    'config': path.resolve('./src/config', 'config.json'),
    'migrations-path': path.resolve('./src', 'migrations'),
    'models-path': path.resolve('./src', 'models'),
    'seeders-path': path.resolve('./src', 'seeders')
    }
------
    'models-path': path.resolve('./src', 'models'),
> nó giúp ta tạo file models trong src
----
    'seeders-path': path.resolve('./src', 'seeders')
>seed --> giúp tạo dữ liệu fake
----
    'migrations-path': path.resolve('./src', 'migrations'),
>migrations -->tạo bảng với mysql qua câu lệnh ngắn gọn trên terminal
---
    'config': path.resolve('./src/config', 'config.json'),
> nói cho biết lấy database từ đâu
---
    return queryInterface.bulkInsert('User',[{
        firstName: 'john',
        lastName: 'Doe',
        email:'example@gmail.com',
        createdAt: new Date(),
        updatedAt: new Date()
        }])
> thêm câu lệnh này vào phần up câu file seeders
> giúp ta quay lại dc database trước đó  

---

**tiep tuc chay cau lenh nay:  npx sequelize-cli db:seed:all**
    npx sequelize-cli db:seed:all


### has password ->max hoas mat khau
    npm i --save bcrypt@5.0.1

>ví dụ

        let hasUserPassword = (password) => {
            return new Promise(async (resolve, reject) => {
                try {
                    let hasPassword = await bcrypt.hashSync(password, salt)
                    resolve(hasPassword)
                } catch (err) {
                    reject(err)
                }
            })
        }

--> dùng : hasUserPassword(data.password)



## jsonWebToken - jwt
step1: npm i jsonwebtoken

step2: create file jwt and import

===> sign() --> tạo mã token

===> verify() --> check mã token nếu đúng thì cho qua sai thì dừng 

--> middleware jwt -->ứng dụng làm login,, phân quyền user 

**cấu trúc**

token = header.payload.signnature

data + secret (sign) => token

token + secret (verify) => data


> ví dụ:

        jwt.sign({data: 'foobar'}, 'secret', { expiresIn: '1h' });
        hoặc
        ----->user là data truyền vào 
        jwt.sign({data:user},process.env.ACCESS_TOKEN, {
            algorithm:"HS256",
            expiresIn:process.env.TOKEN_TIME_LIFE
        },

> ví dụ:

        jwt.verify(token, 'secret', function(err, decoded) {
        console.log(decoded.foo) // bar
        });

//update continue


## Cài đặt OpenSSL, sử dụng tạo private key và public key
===> mã hóa secret bthg là chuỗi kí tự thì ngta có thể dung tool tra ra rất nhanh 
nhưng với ssl thì nó là cả 1 đoạn văn bản rất khó để hack 

- secret coi như là mật khẩu 

- tải thư viện ssl để tạo mật khẩu bảo mật với ssl

- https://slproweb.com/products/Win32OpenSSL.html

- nếu cài các bản kia k dc thì cài bản 1.1 light

- cấu hình set môi  trg

- vào tìm kiếm của máy tìm: environment --> chọn edit -> environment variable --> chọn path của system variable -> chọn new -> dán câu này vào và ok --> C:\Program Files\OpenSSL-Win64\bin

- check thử xem dc chưa --> cmd gõ openssl --> nếu ra openssl> là đã cài dc 

- openssl generate private key and public key
hoặc

- https://stackoverflow.com/questions/44474516/how-to-create-public-and-private-key-with-openssl

> 2 link này có câu lệnh tạo private key

- vào thư project tạo thư mục key -> vào thư mục key -> cmd --> dán câu lệnh này vào để tạo key

- tạo private key --> openssl genrsa -out private.pem 2048 --> không có thông tin gì
- tạo private key có thông tin --> openssl req -newkey rsa:2048 -nodes -keyout domain.key -out domain.csr

- tạo public key từ private key --> openssl rsa -in keypair.pem -pubout -out publickey.crt
- tạo public key từ private key có thông tin --> openssl req -key domain.key -new -out publickey2.csr

- https://www.npmjs.com/package/jsonwebtoken

        var privateKey = fs.readFileSync('private.key');
        var token = jwt.sign({ foo: 'bar' }, privateKey, { algorithm: 'RS256' });


>ví dụ:

    var jwt = require('jsonwebtoken')
    var fs = require('fs')
    var privateKey = fs.readFileSync('./key/private.pem');
    // var token = jwt.sign({ foo: 'bar' }, privateKey, { algorithm: 'RS256' });
    // console.log(token);
    const token = "token vừa tạo"
    ví dụ:
          var token = "eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJmb28iOiJiYXIiLCJpYXQiOjE2ODM5OTY2OTZ9.e_CCVaecs0YngD5UGhtgOeu7695AcVFlqlSkd8IJmUzhUrT-XzVApFOgh0Bmj4nvBtwnRBT2AFJD09oqHeNr9QP6Cmu8GSb_LSOP96Hl3k42HuIjsezzCyE7a0BNUvEQgO1EgTRFpND5fugCzDPmQMrpYv7YwuJAugHNEzWtdQJKn6lW9FwpeUro-Ya8ZN88oItW3H6VFU9BcekzOKHDShuEJw1R49xA6X6emMuQDfCYTQ3ciYS0KRqT97NADbpNCli7vHnspeKvCeLfj5xZjmzG1AqFT5xMm9LLJ5AJnmUGg_Gb92XnPIloqC8fSgQLi8pg_ISBcAN2aOdbiDWhiw"

    var cert = fs.readFileSync('./key/publickey.crt'); 
    const kq = jwt.verify(token, cert, { algorithms: ['RS256'] })
    console.log(kq);

## promise

    --> new Promise((re, rj)={})
    .then: chỉ dc gọi khi rs hoặc rj thực hiện xong
    .catch()

    async await 
    await new Promise
    :bắt tất cả thằng bên dưới phải đợi

    xử lí lỗi
    Promise.catch
        async 
        try {}catch(){}



    var pr1 = new Promise((resolve, reject )=>{
    fs.readFile('', (err, data)=>{
        if(err) reject(err)
        else resolve(data)
    })
    })
    .then((data)=>{
    return p2
    })
    <!-- return cái gì thì .then sau nhận dc cái đó -->
    .then((data)=>{
    return p3
    })
    .then((data)=>{
    return p4
    })
    .catch((err)=>{
    console.log(err )
    })

    async (req, res)=>{
    var kq = await pool.excute('select* from users where id=?', [ id])
    }

    try {
    // code đông bộ await ....
    }catch(err)=>{
    console.log(err)
    }

## Session cookie và cài đặt redis
**cookie**
- link: https://www.w3schools.com/js/js_cookies.asp
- viết trong cặp script

        function setCookie(cname, cvalue, exdays) {
            const d = new Date();
            d.setTime(d.getTime() + (exdays * 24 * 60 * 60 * 1000));
            let expires = "expires=" + d.toUTCString();
            document.cookie = cname + "=" + cvalue + ";" + expires + ";path=/";
        }
        function getCookie(cname) {
            let name = cname + "=";
            let decodedCookie = decodeURIComponent(document.cookie);
            let ca = decodedCookie.split(';');
            for (let i = 0; i < ca.length; i++) {
                let c = ca[i];
                while (c.charAt(0) == ' ') {
                    c = c.substring(1);
                }
                if (c.indexOf(name) == 0) {
                    return c.substring(name.length, c.length);
                }
            }
            return "";
        }
        setCookie('username', 'tuanflute', 1)

- muốn xóa  cookie thì thay 1 thành -1 , nó chỉ là nơi lưu trũ có thời gian hết hạn , 1 là 1 ngày

**Session**

- link: https://www.npmjs.com/package/express-session
- npm i express-session
- download redis -->  https://github.com/microsoftarchive/redis/releases/tag/win-2.8.2104
- npm i connect-redis
- npm i redis

## passportJS Local và Bearer Token  
- https://www.passportjs.org/ --> nó tạo ra 1 kịch bản 
- **ví dụ**: nó cho phép đăng nhập bằng fb , gg ... thì nhờ fb  xác thực hộ và quay về server tạo jwt để xác thực k cần tạo tk bthg nữa 
- chức năng đang nhập bằng bên thứ 3

        npm i passport passport-local

> ví dụ:

        var passport = require('passport')
        var LocalStrategy = require('passport-local').Strategy


## Starpi Nodejs