# laravel

    https://laravel.com/

# download composer

    https://getcomposer.org/download/

# download laravel

    composer create-project laravel/laravel:^9.0 example-app

# config xampp

step 1: open button config apache

step 2: click PHP (php.ini)

step 3: click edit -> find zip

step 4: remove mark ; at left

# extension

laravel artisan -> quản lý cake, database...

laravel blade snippets -> tự động chấm sổ, tự động mở ngoặc đóng ngoặc...

laravel blade spacer -> tự động mở đóng object

laravel goto view -> bấm vào đường dẫn chứa view thì nó sẽ nhảy thẳng đến view đấy

laravel extra intellisense -> k biết

live sass compiler -> hỗ trợ css

Beautify css/sass/scss/less -> format css

PHP IntelliSense 

Getter and Setter Generator 

Bracket Pair Color DLW 

# terminal 
composer update , composer install, ...

php artisan list -> xem tất cả các lệnh hỗ trợ của laravel

php artisan make:controller ProductsController   -> để tạo 1 controller , nếu chạy thêm lần nữa nó sẽ báo k dc

php artisan make:controller ProductsController --force -> tạo thêm 1 controller trùng tên


//route web
// use ProductsController

    Route::get('/products', [
        ProductsController::class,
        'index' // index function of productsController
    ]);

controllers

    class ProductsController extends Controller
    {
        public function index()
        {
            // truyền dữ liệu xuống view cách 1
            $title =  'tuanflute275-bkap';
            // return view('products.index', compact('title'));


            // truyền dữ liệu xuống view cách 2   
            return view('products.index')->with('title' , $title);

            with(key, value); -> chỉ truyền dc 1 parameter
            compact('title', 'x'..); -> truyền dc nhiều parameter

              //truyền 1 mảng
             $myPhone = [
                 'name' => 'iphone 14',
                 'year' => 2022
              ];
              return view('products.index', compact('myPhone'));
             }
        }

view blade

    @foreach ($myPhone as $item)
        <h3>{{ $item }}</h3>
    @endforeach

get by id and validate

    Route::get('/products/{id}', [
        ProductsController::class,
        'details'
    ])->where([
        'id', '[0-9]+',
        'productName' => '[a-zA-Z0-9]+'
    ]);

        //controller
      public function details($id) {
        echo "Chi tiết sản phẩm ".$id;
    }

# Configure Header and Footer of a View using app layout
trong thư mục views tạo ra 1 thư mục layouts để làm layout chính cho trang web
trong layouts có các file như sau: header.blade.php, footer.blade.php, app.blade.php

 header.blade.php -> chứa template của header
 footer.blade.php -> chứa template của footer
 app.blade.php -> cấu hình trang mặc định của web chứa header và footer 

 //các template content

    @extends('layouts.app');

    @section('content')
        <h1>this is about page, hi</h1>
    @endsection


app.blade.php

    <!doctype html>
    <html lang="en">
    <head>
        <title>index</title>
        <!-- Required meta tags -->
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

        <!-- Bootstrap CSS -->
        <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css">

        <style>
            .active {
                color: red !important;
            }
        </style>
    </head>
    <body>
        {{-- //include file header vào --}}
        @include('layouts.header')

        {{-- layout chung cho trang web và  @yield('content') coi như router-outlet angular --}}
        @yield('content')

        {{-- //include file footer vào --}}
        @include('layouts.footer')

        <!-- Optional JavaScript -->
        <!-- jQuery first, then Popper.js, then Bootstrap JS -->
        <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"></script>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js"></script>
        <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js"></script>
    </body>
    </html>



# Configure Navigation and nav-item

            <li class="nav-item">
                <a class="nav-link {{ request()->is('/') ? 'active' : '' }}"
                href="/">Home</a>
            </li>
            <li class="nav-item">
                <a class="nav-link {{ request()->is('about') ? 'active' : '' }}"
                href="/about">about</a>
            </li>

# IMAGE 

    @extends('layouts.app')

    @section('content')
        <h1>page index</h1>
        {{ print_r(URL('')) }}
        <img src="{{ URL('images/pen.jpg') }}" alt="">
    @endsection

# Save images to Storage 
 php artisan storage:link
 sau đó
 lưu ảnh trong thư mục storage trong thư mục public

    <img src="{{ asset('storage/pen.jpg') }}" alt="">  


# Some basic commands-syntax in Laravel Blade - Một số cú pháp lệnh cơ bản trong Laravel Blade

    x = {{ $x = 20 }}
    @if ($x < 10)
        <h3>x nhỏ hơn 10</h3>
    @elseif($x > 10)
        <h3>x lớn hơn 10</h3>
    @else
    <h3>all conditions does not match</h3>
    @endif

    <!-- kiểm tra dữ liệu truyền từ controller có rỗng hay không -->

     {{-- unless = if not --}}
    @unless (empty($name))
        <h3>name is not empty</h3>
    @endunless

     {{ if not }}
    @if(!empty($name))
        <h3>name is not empty</h3>
    @endif

    {{ empty }}
    @empty(!$name)
        <h3>ahah</h3>
    @endempty

    {{ switch - case }} 
   @switch()
       @case()

           @break

       @default

    @endswitch


    {{ for }}

      @for ($i = 0; $i < 20; $i++)
        <h2>i = {{ $i }}</h2>
        @endfor

    {{ foreach }}

      @foreach ($names as $name)
         <h3>{{ $name }}</h3>
      @endforeach

    {{-- vòng lặp while --}}
        {{ $i = 0 }}
    @while ($i < 10)
        <h3>i = {{ $i }}</h3>
        {{ $i++ }}
    @endwhile

# Add SASS in a Laravel Project


# Add MySQL Database using XAMPP
php artisan make:controller PostController

php artisan make:model Post

php artisan make:migration create_table_post

php artisan make:model -m    -> -m : migration


## config laravel

* config date
- vào file app.php trong thư mục config tìm tới timezone 
- sửa UTC -> 'timezone' => 'Asia/Ho_Chi_Minh',

## router 
    Route::get('/about', [PagesController::class, 'about'])->name('about');   -> đặt tên cho router với ->name()

router với tham số

    Route::get('/test/{id?}', function($id=null){
        return 'pages.test '.$id;
    })->where([
        'id' => '[0-9]+'
    ]);

## controller 
- câu lệnh tạo nhanh crud controller : 

    php artisan make:controller PhotoController --resource

      public function __construct(){}  = hàm này sẽ chạy đầu tiên giống như OnInit bên angular

## Middleware

    // Admin routes
    Route::middleware('auth.admin')->prefix('admin')->group(function() {
        Route::get('/', [DashboardController::class, 'index']);
        Route::resource('product', ProductController::class)->middleware('auth.admin.product');
    })

- tạo middleware với câu lệnh :  php artisan make:middleware name_middleware
- import middleware vào file Kernel.php
    +  protected $middleware = []  -> import ở đây là global middleware cho tất cả request
    + protected $middlewareGroups = [
        'web' : middleware cho các router của web.router.php,
        'api': middleware cho các api
    ]
- Route::middleware('auth.admin') : middleware có tên là auth.admin sẽ dc áp dụng cho cả group admin
- Route::resource('product', ProductController::class)->middleware('auth.admin.product');  = middleware với tên auth.admin.product sẽ dc áp dụng với resource , áp dụng với 1 router đơn lẻ
-prefix->group() : gộp tất cả các router thành 1 router có path chung , ví dụ ở trên path chung lad admin

## View trong laravel


## http request

   public function req(Request $request){
        $allData = $request->all();
        dd($allData);
    }
$request->all()  = lấy ra tất cả dữ liệu

$request->path() = lấy path của url trừ tên miền

$request->is() = kiểm tra xem url có khớp hay không

      if($request->is(categories)){
            return 'chuoi nsay chi co path categories nhận dc'
        }

$request->url() = lấy ra url hiện tại nhưng k lấy ra query string , phần sau dấu hỏi  ví dụ : ?name=tyhd

$request->fullUrl() = lấy ra full url hiện tại

$request->method() = lấy ra method hiện tại

$request->ip() = lấy ra địa chỉ ip

$request->serve() = lấy ra thông tin

$request->header() = lấy ra thông tin header

$request->input() = lấy thông tin url nhg có 1 vài cái laravel hỗ trợ 

    $request->input('id.*.name');

dd(request());

$request->query('id');  = lấy ra query

$request->has('cate_name');  = kiểm tra xem có name nào tên cate_name không ??

$request->flash();  lưu data từ input vào session trong  1 time ngắn

$request->file();  = lấy ra thông tin file

## view engine blade
- @csrf tạo ra token là hàm có sẵn laravel 

    ```
    <form action="" method="post">
        <input type="text" name="username" id="">
        @csrf
        <button type="submit">submit</button>
    </form>

 - method put trong laravel

    ```  
    <form action="" method="post">
        <input type="text" name="username" id="">
        <button type="submit">submit</button>
        @csrf
        @method('PUT')
    </form>

-stack - push - prepend 
 
 trong layout chính khai báo @stack(name) -> ví dụ: @stack('scripts');

 trong file cần thêm mới js thêm câu lệnh, push nó sẽ gom tất cả các script trong @push vào cuối layout chính

    @push('scripts')
        console.log('ok');
    @endpush

- trong file cần thêm mới js thêm câu lệnh, push nó sẽ gom tất cả các script trong @push vào đầu layout chính

    @prepend('scripts')
        console.log('ok lan 2');
    @endprepend

-component : tái sử dụng 1 mẫu html nào đó nhiều lần

## http response

    Route::get('demo-response', function(){
        1//$response = new Response('hey', 201);
        2//$response = response('hey', 201);
        return $response;
    });

-cookie response

    Route::get('demo-response', function(){
       $response = (new Response())->cookie('cookie', 'hello cookie', 30);
        return $response;
    });
    Route::get('demo-response-2', function(Request $request){
        return $request->cookie('cookie');
    });

-json response

    Route::get('demo-response', function(){
      $arr = ['hi', 'hello', 'halo']
        return response()->json($arr, 201)->header('Api-key', '123');
    });

-response dạng chuyển hướng

    Route::get('demo-response', function(){
        return redirec('admin/them-san-pham');
    });

    Route::post('demo-response', function(Request $req){
        if(!empty($req->$username)){
            return redirect(route('demo-response'))->with('message', 'success');
        }
    });

-response download file

    public function downloadImage(Request $request) {
            if(!empty($request->$image)){
                $image = trim($request->$image);

                $fileName = 'image_'.uniqid().'jpg';  // download voi ten random

                $fileName = basename($image); // download voi ten goc

                return response()->streamDownload(function() use($image){
                    $imageContent = file_get_contents($image);

                }, $fileName);
            }
        }


## Validation trong Laravel

https://laravel.com/docs/10.x/validation#manually-creating-validators

## database
 file image.rar

## Laravel Artisan Console là gì? 
Laravel Artisan Console
Artisan là tên của giao diện màn hình gõ lệnh đính kèm trong Laravel. Nó cung cấp một danh sách các câu lệnh hữu ích để sử dụng trong quá trình phát triển sản phẩm. Artisan được phát triển dựa trên component Symfony Console khá mạnh mẽ. Để xem danh sách các câu lệnh được cung cấp, bạn có thể sử dụng câu lệnh list;

    php artisan list

    php artisan help migrate/make:controller...
