## import library reactJs

    <script src="https://unpkg.com/react@17/umd/react.development.js" crossorigin=""></script>
    <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js" crossorigin=""></script>
ví dụ

    const h1React = React.createElement('h1', {
        title: 'hello',
        className: 'h1test'
    }, 'hello guys')

    const ulReact = React.createElement(
        'ul',
        {
            id: 'ul-li',
        },
        React.createElement('li', { id: 'first-li' }, 'item1'),
        React.createElement('li', null, 'item2')
    )
> render html ==> ReactDOM.render(h1React, document.getElementById('root'))

## JSX - babel
-->chuyển đổi cú pháp es6 to es5 
***
ví dụ

    <script type="text/babel">
        const ulBabel = <ul>
            <li>li-1</li>
            <li>li-2</li>
            <li>li-3</li>
        </ul>
        ReactDOM.render(ulBabel, document.getElementById('root'))
    </script>

**react không thể render 2 element cùng lúc như ví dụ dưới đây được**
example

    const jsx = (
        <h1>hello 1</h1>
        <h2>hello 2</h2>
    )
    ReactDOM.render(jsx, document.getElementById('root'))

--> mà nó phải đc bọc trong 1 khối , react chỉ render 1 khối 
***
ví dụ --> thay vì là thẻ div => React.Fragment thẻ này sẽ ẩn chỉ còn những thẻ trong nó hiện ra khi f12

    const jsx = (
        <React.Fragment>
            <h1>hello 1</h1>
            <h2>hello 2</h2>
        </React.Fragment>
    )
    ReactDOM.render(jsx, document.getElementById('root'))

## React components
ví dụ về component function

    function Header() {
            return (
                <div class="header">header</div>
            )
        }
        const app = (
            <div class="wrapper">
                <Header />
                <div class="main">main</div>
                <div class="footer">footer</div>
            </div>
        )
    ReactDOM.render(app, document.getElementById('root'))

## Props
ví dụ

    function PostItem(props) {
            props.callback(Math.random())
            return (
                <div className="post-item">
                    <h1>{props.h1}</h1>
                    <h3>{props.h2}</h3>
                </div>
            )
        }
        function App() {
            return (
                <div id="wrapper">
                    <PostItem
                        h1='xin chào tất các bạn '
                        h2='mình là sinh viên năm nhất '
                        callback={(random) => {
                            console.log('random:', random);
                        }}
                    />
                </div>
            )
        }

        ReactDOM.render(<App />, document.getElementById('root'))
 không truyền dc key
 ***
 class => className
 ***
for ==>htmlFor - with label input


## router 
npm i react-router-dom redux react-redux redux-thunk

-- react router: chuyển hướng trang web

-- react-redux : để sử dụng redux

-- redux-thunk: để xử lý bất đồng bộ

##
component là các thành phần của 1 trang web k có router
container có router là các trang ghép từ component và thêm nữa
trong container có thư mục public => k cần đăng nhập  , system => phải đăng nhập

folder ultis để lưu các const 

***

    import { useState } from "react";
    import { useSelector, useDispatch } from "react-redux";
    // useSelector :  lấy dữ liệu từ redux
    // useDispatch : mang action tới redux

    import { Home, Login, Public } from './containers/public/'
    import { Routes, Route } from 'react-router-dom'


    function App() {
    const { test } = useSelector(state => state.app)
    console.log(test)
    return (
        <>
        <div className="App">
            <Routes>
            <Route path="/*" element={<Public />}>
                <Route path="home" element={< Home/>}/>
            </Route>
            </Routes>
        </div>
        </>
    );
    }

    export default App;


--> viết 1 thẻ đóng Route thôi cx dc nhưng ở đây là có những route con ở bên trong nên viết thế này cho tường minh

--> path="/*" ==> sau dấu / là gì thì cũng redirec về Public 

--> path bên trong public k cần / vì nó lấy thằng to nhất cộng với path 

## outlet

    import React from "react";
    import { Outlet } from "react-router-dom";

    const Public = () => {
        return (
            <div>
                public
                <Outlet/>
            </div>
        )
    }

    export default Public
--> khi truy cập vào thằng con của public sẽ hiện ra phần tử con đấy

## extension ES7 React/Redux/GraphQL/React-Native snippets
rafe => cấu trúc function nhanh

## npm i react-icons 
- giống font https://fontawesome.com/

## Cài đặt tailwind css 
step 1 : npm install -D tailwindcss postcss autoprefixer 
step 2 : npx tailwindcss init -p

    /** @type {import('tailwindcss').Config} */
    module.exports = {
    content: [
        "./src/**/*.{js,jsx,ts,tsx}",
        "./public/index.html"
    ],
    theme: {
        extend: {},
    },
    plugins: [],
    }
--> cấu hình những đuôi file nào sẽ dùng tailwindcss dc

## Cài đặt sass/scss
npm i node-sass@4.14.1

hoặc sử dụng module.css -> tạo tên class đặc biệt
import styles from './Button.module.css'; 
sử dụng : className={styles.button}