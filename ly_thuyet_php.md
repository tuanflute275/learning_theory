## SETUP PHP.
- cài xampp làm môi trường chạy code 
- vào phần htdocs -> tạo thư mục và file php
> ví dụ: htdocs\bai1\index.php

> install extension run code on vs code -> chạy php


## EXTENSION PHP

1.PHP Intelephense
===> extension setting --> edit in setting.json

    "php.validate.enable": true,
    "php.validate.executablePath": "đương dẫn của xampp (vi dụ : c://xampp)",

2.PHP Server

### PHP

Được viết trong cặp từ
câu lệnh echo để hiện ra
phải có dấu ; ở cuối

    <?php
    //code
    echo phpInfo();

muốn viết html thì phải đóng ngoặc đoạn code php

    <?php
    code
    ?>

### VARIABLE - BIẾN PHP

Cú pháp : $tên_biến -- giống sass

>ví dụ: $name
đặt tên theo quy tắc đặt tên biến thg

- bắt đầu là 1 chữ hoặc dấu gạch dưới
  -đặt theo kiểu nối nhau là dấu gạch dưới hoặc từ thứ hai trở đi viết hoa chữ cái đầu

>ví dụ

    <?php
    $name: 'nguyen van a'
    echo $name
    ?>

## DEBUG DỮ LIỆU

var_dump($var): trả về kiểu dữ liệu và giá trị
print_r($var): thường dùng in ra mảng và đối tượng
>ví dụ

    var_dump($name): nhận về string(12) "nguyen van a"

 có thể truyền vào biến như ở trên hoặc số chuỗi luôn

## CÁCH NỐI BIẾN TRONG PHP

nối với nhau bằng dấu **.**

Cú pháp: $bien1.$bien2

>ví dụ 1

    $bien1 = 'nguyen van a';
        $bien2 = '18';
        $bien3 = 'tuổi';
        echo $bien1.' '.$bien2.' '.$bien3;
        echo 'tôi tên là: '.$bien1;

$test = "sử dụng dấu {} để đóng goi biến tránh k hiển thị ví dụ: {$bien1}";
echo $test;

---

>ví dụ 2

    $url = 'https://www.facebook.com/home.php';
    $imgUrl = 'link img';
    $htmlOutput =   '<a href="'.$url.'"><img src="'.$imgUrl.'"></a>';
    echo $htmlOutput;

nên để dấu nháy đơn vì trong html để dấu " rồi
cách nối php trong html

href="link" ===> $bien=link ==>href="'.$bien.'"
-- trong dấu " thêm 2 dấu ' và .

### HẰNG SỐ

**Cú pháp**: define ('ten_hang', 'giá trị');
sử dụng: ten_hangví dụ

    define ('_LINK_FB','https://www.facebook.com/home.php');
    echo _LINK_FB;

hoặc

    const _link_fb = 'https://www.facebook.com/home.php';

kiểm tra hằng số

    $checkDefine = defined('_LINK_FB');
    var_dump($checkDefine);

### CÁC KIỂU DỮ LIỆU TRONG PHP

1. INT

- Khai báo biến kiểu int: $ten_bien = so_nguyen
    ép kiểu int: (int)$ten_bien
- kiểm tra số nguyên: is_int($ten_bien ) hoặc is_integer($ten_bien)
> ví dụ
// khai báo

     $age = 20.8;
      // ép kiểu
      $age = (int)$age;
      var_dump($age);

2. KIỂU SỐ THỰC\_
- Khai báo biến kiểu float: $ten_bien = so_thuc(co dau phảy)
    ép kiểu float: (float)$ten_bien
- kiểm tra số thực: is_float($ten_bien)

3. KIỂU STRING

- Khai báo biến kiểu string: $ten_bien = 'chuỗi' hoặc "chuỗi"
- kiểm tra kiểu string: is_string($ten_bien)

>ví dụ

    $message = 'every one';
    $message = (string)$message;
    $checkString = is_string($message);
    var_dump($message);
            var_dump($checkString);

4.  KIỂU BOOLEAN

- khai báo kiểu dữ liệu:$ten_bien = giá trị boolean 
-    ép kiểu boolean: (boolean)$ten_bien hoặc (bool)$ten_bien 
-  các kí tự 0, trống, null quy về false ngược lại là true
- kiểm tra kiểu boolean: is_bool($ten_bien )
>    ví dụ

        $check = true;
        $check = is_bool($check);
        // ép kiểu
        $check = (bool)$check;
        var_dump($check);

5.  KIỂU MẢNG\_

-    khai báo:$ten_bien = array()
-    ép kiểu mảng: (array)$ten_bien
-    kiểm tra kiểu mảng: is_array($ten_bien )
 >   ví dụ

        $carArr = [];
        $carArr = (array)$carArr;
        $checkArr = is_array($carArr);
        var_dump($carArr);
        var_dump($checkArr);

6.  KIỂU NULL

-    khai báo: $ten_bien = null
-    ép kiểu sang int  => 0;
-    ép kiểu sang string  => rỗng;
-    ép kiểu sang boolean  => false;
-    kiểm tra kiểu null: is_null($ten_bien )

---

>ví dụ

    $total = null;
    $total = (int)$total;
    $total = (boolean)$total;
    $total = (string)$total;
    $total = (array)$total;
    $checkNull = is_null($total);
    var_dump($total);
    var_dump($checkNull);

7. KIỂU RESOURCE

-   kiểu dl đặc biệt, nó lưu trữ tham chiếu đến các hàm - tài nguyên bên ngoài php : file , database..
 -  kiểm tra kiểu RESOURCE: is_resource($ten_bien )

---

ví dụ

    $curl = curl_init();
    $checkType = get_resource_type($curl);
    var_dump($curl);
    var_dump($checkType);

8. KIỂU ĐỐI TƯỢNG (OBJECT)

-   ép kiểu đối tượng từ mảng: (object)$bien_mang
kiểm tra kiểu đối tượng: is_object($ten_bien)

---

ví dụ

    $dataCus = ['tunanan'];
    $dataCus = (object)$dataCus;
    $checkOb = is_object($dataCus);
    var_dump($dataCus);
    var_dump($checkOb);

PHÂN biệt empty và null

    $message = null; //rỗng -->giữ chô k tốn bộ nhớ
    $message = ''; //trống --> vẫn cần bộ nhớ trong ram

## TOÁN TỬ VÀ BIỂU THỨC TRONG PHP

1.Toán tử gán: = , +=, -=, _=, /=, %=, .=
2.Toán tử số học: +, -, _, /,%, ++, --, \*\* 3. Toán tử so sánh: > , >=, <, <=, ==, ===, !=
4.Toán tử lý luận: &&, ||, !

## IF - ELSE PHP

Cấu trúc:
if(condition){
//code
}else{
//code
}

---

ví dụ

        $number = 15;
        if($number){
            if($number%2==0){
                echo $number.' là số chẵn';
            }else if($number%3==0){
                echo $number.' là số lẻ';
            }else{
                echo $number.' là số không kiểm tra điều kiện được';
            }
        }else{
            echo 'không có tham số truyền vào';
        }

## switch - case

switch(gia_tri){
case:
default:
}

---

ví dụ

    $month = 2;
    $year = 2021;
    $year = (int)$year;
    switch($month){
        case 1:
        case 3:
        case 5:
        case 7:
        case 8:
        case 10:
        case 12:
            echo 'tháng có 31 ngay';
        case 4:
        case 6:
        case 9:
        case 11:
            echo 'tháng có 30 ngày';
        case 2:
            // code kiem tra tháng 2 chỉ là tượng trưng
            if(time()){
                echo 'tháng có 29 ngày';
            }else{
                echo 'tháng có 28 ngày';
            }
        default:
            echo 'Số tháng nhập vào không hợp lệ';
    }

## loop - FOR

for($ten_bien = gia_tri_dau; dk_ket_thuc; bieu_thuc_tang){
//code
}

---

ví dụ

        for($i; $i<10; $i++){
            echo 'vòng lặp thứ '.$i.'<br/>';
        }

thay thế

    for($i; $i<10; $i++)
    echo 'vòng lặp thứ '.$i.'<br/>';
    endfor;

## LOOP - WHILE

==> DK SAI KHONG CHAY
while(dieu_kien_dung){
//code
}

---

ví dụ

        $i = 0;
        while($i<10){
            echo 'đây là vòng lặp while thứ '.$i.'<br/>';
            $i++;
        }

## LOOP - DO-WHILE

==> vẫn chạy ít nhất 1 lần kể cả dk sai

        do{
            //code
        }while(dieu_kien_dung);

---

ví dụ

---

        $i = 0;
        do{
            echo 'đây là vòng lặp do while thứ '.$i.'<br/>';
            $i++;
        }while($i>10);

## break - continue - die - exit

---> break : thoát khỏi vòng lặp ->thoát khoi
--->continue: bo qua vòng lặp ->bỏ qua
---->break và continue dùng trong if else or switch case
--->exit và die --> code nằm bên dưới ctrinh sẽ bỏ qua kể cả f12

## câu lệnh Include - Include once - Require - Require once

LỆNH INGLUDE - INCLUE_ONCE = REQUIRE - REQUIRCE_ONCE

4 lệnh: include, include_once, require, require_once dùng để import file php khác
vào php đang chạy

Cú pháp chung: include 'path_to_php.\_file' hoặc include ('path_to_php. file);
inelude: Import file khác, nếu import lỗi => các câu lệnh bên dưới vẫn chạy.

include_ones: Import file khác, chỉ import 1 lần, nếu import lỗi => các câu lệnh
bên dưới vẫn chạy

require: Import file khác, nếu import lỗi => Các câu lệnh bên dưới sẽ dừng.
require_once: Import file khác, chỉ import 1 lần, nếu import lỗi => Các câu lệnh
bên dưới sẽ dừng

ví dụ

    <?php
    // include --> là import file

    // $path = __DIR__.'/include'; // đường dẫn tuyệt đối
    $path = 'include'; // đường dẫn tương đối file home phải ngang hàng với các file include , nếu file home.php nằm trong 1 thư mục nào đó k còn ngang hàng với thư mục include thì lỗi
    include $path.'/header.php';
    include_once $path.'/header.php'; // include_once nếu cùng 1 file thì chỉ import dc 1 lần , còn khác file thì vẫn bthg
    echo "đây là nd them";
    include $path.'/content.php';
    include $path.'/footer.php';

    // REQUIRE
    require $path.'/header.php';
    require_once $path.'/header.php'; // require_once nếu cùng 1 file thì chỉ import dc 1 lần , còn khác file thì vẫn bthg
    echo "đây là nd them";
    require $path.'/content.php';
    require $path.'/footer.php';

    // khác nhau khi lỗi đường dẫn => đối với include thì các câu lệnh trong file home này vẫn hoạt động => ví dụ nó sẽ vẫn chạy câu echo trong file này mặc dù include 3 file kia lỗi
    // đối với require khi lỗi đường dẫn thì k hiện mà ẩn hết đi, chương trình bên dưới k chạy;

    // => nên sử dụng require hoặc require_once

## toán tử 3 ngôi

    $number = 1;
    $print = $number == 10 ? 'bạn đã đủ tuổi' : 'bạn chưa đủ tuổi';
    echo $print;

## Xử lý chuỗi trong PHP

    $name = 'nguyen van a "lop c2208g" ';
    echo '</br>';
    echo $name;

-> chuỗi bên trong phải khác dấu bên ngoài -> bên trong nháy kép thì bên ngoài nháy đơn và ngược lại
-> nếu bắt buộc cả 2 cùng dấu thì để dấu \

    $name = 'nguyen van a \'lop c2208g\' ';
    echo '</br>';
    echo $name;

---

nối chuỗi -> dùng dấu .

    $name = 'nguyen van a ';
    echo '</br>';
    echo $name.'18 tuổi';

các hàm cơ bản với chuỗi

    <?php
    // addcslashes(chuỗi, kí tự) // => thêm kí tự \ vào trước kí tự mình muốn
    $str = 'tuan flute 275';
    // $str = addcslashes($str, 'ef');
    $str = addcslashes($str, 'f"');
    // addslashes => thêm kí tự vào trước dấu ', ", \
    $str = addslashes($str);
    //stripcslashes => loại bỏ tất cả dấu \ đã dc thêm vào
    $str = stripcslashes($str);
    echo $str;
    echo '</br>';

    // chuyển chuỗi thành mảng explode
    // explode('dựa_vào_kí_tự_nào ', chuỗi_cần_chuyển)
    $str2 = 'tuan flute 275';
    $arr = explode(' ', $str2);
    print_r($arr);
    echo '</br>';

    // chuyển mảng thành chuỗi implode
    // implode('dựa_vào_kí_tự_nào ', mảng_cần_chuyển)
    $str = implode(' ', $arr);
    echo $str;

    // lấy độ dài của chuỗi
    $str = 'tuan flute';
    echo '</br>';
    echo 'độ dài của chuỗi là: ';
    $length = strlen($str);
    echo $length;

    // lặp chuỗi theo số lần xác định
    $str = "tuan275";
    $str = str_repeat($str, 10);
    echo $str;
    echo '</br>';

    // hàm tìm kiếm và thay thế replace
    $str = 'tui la tuan hoc sinh lop c2209h';
    $str = str_replace('c2209h', 'c2208g', $str);
    echo $str;
    echo '</br>';

    // hàm mã hóa 1 chiều 32 kí tự
    $str = '12345';
    $str = md5($str);
    echo $str;
    echo '</br>';

    // hàm mã hóa 1 chiều 40 kí tự
    $str = '12345';
    $str = sha1($str);
    echo $str;
    echo '</br>';

    // hàm chuyển chuỗi thành dạng thực thể
    $str = '<p>hello php</p>';
    $str = htmlentities($str);
    echo $str;
    echo '</br>';

    // hàm chuyển dạng thực thể sang html
    $str = '<p>hello php</p>';
    $str = html_entity_decode($str);
    echo $str;
    echo '</br>';

    // hàm loại bỏ thẻ html
    $str = '<p><a href="http://facebook.com">fb </a>hello php</p>';
    $str = strip_tags($str); // loại bỏ tất các thẻ html
    $str = strip_tags($str, '<a>'); // loại bỏ thẻ htmln trừ thẻ a
    echo $str;
    echo '</br>';

    // hàm cắt chuỗi
    $str = 'lorem dsfgsdnhbfashjkfq.gdzfhasgf.ehjsdfwe';
    $str = substr($str, 0, 6); // cắt chuỗi nào từ vị trí nào đến vị trí nào
    $strstr = strstr($str, '.'); // cắt chuỗi từ chuỗi cho trc bắt dầu từ kí tự nào
    echo $str;
    echo $strstr;
    echo '</br>';

    // tìm chuỗi và trả về số thứ tự
    $str = 'tuan flute 275';
    $str = strpos($str,'flute');
    var_dump($str);
    var_dump($str);
    echo '</br>';

    // replace 1 đoạn trong chuỗi
    $str = 'tuan flute 275';
    $str = substr_replace($str,'2004',11 ); //  substr_replace(chuỗi, chuỗi thay thế, vị trí, độ dài)
    echo $str;
    echo '</br>';

    //
    $str = 'tuấn flute 275';
    $str = strtolower($str);  // chữ thường --> k hỗ trợ tiếng việt có dấu
    $str = trim($str); // xóa kí tự 2 bên ltrim xóa bên trái, rtrim() xóa bên phải
    // $str = strtoupper($str); // chữ hoa
    // $str = mb_strtoupper($str); //  hỗ trợ tiếng việt có dấu
    $str = ucfirst($str); // chữ cái đầu tiên của chuỗi viết hoa
    $str = lcfirst($str); // chữ cái đầu tiên của chuỗi viết thường
    $str = ucwords($str); // các chữ cái dầu của chữ => viết hoa
    echo $str;
    echo '</br>';


    // tách chuỗi lớn thành từng chuỗi nhỏ
    $number = '121212';
    $number = chunk_split($number, 2, "-");
    $number = rtrim($number,'-');
    echo $number;
    echo '</br>';

    //chuyển json thành mảng hoặc object
    $str_json = '{"item":"value1", "item2":"value2" }';
    $json_arr = json_decode($str_json);
    print_r ($json_arr);
    echo '</br>';


    //chuyển mảng hoặc object thành json
    $str_json = json_encode($json_arr);
    print_r ($str_json);
    echo '</br>';

## Định nghĩa hàm trong PHP

    function getMessage(...$params){
        print_r($params); // in mảng
        echo '</br>';
        $str = implode(' ', $params); // chuyển mảng thành chuỗi
        echo $str;
    }
    getMessage(1, 2, 3, 4, 5, 6);

-- tham biến : làm thay đổi giá trị truyền vào
-- tham trị : không làm thay đổi giá trị truyền vào

## Hàm Isset - Empty trong PHP

    // hàm isset();
    // kiểm tra biến có tồn tại hay không
    // kiểm tra kiểu dữ liệu của biến
    // không kiểm tra được trường hợp null
    $number = 18;
    var_dump(isset($number) && $number) ;
    if($number){
        var_dump($number);
    }

    // hàm empty()  =>
    // chỉ trả về kiểu dữ liệu boolean
    //không tồn tại => !isset($variable);
    // hoặc
    // rỗng, =0, trống ,null, array rỗng , object rỗng, false
    echo '</br>';
    $str = [];
    $check = empty($str);
    var_dump($check);
    echo '</br>';

    // kiểm tra biến có tồn tại và có dữ liệu ==> dùng phủ định empty nhiều
    $number1 = 18;
    if(!empty($number1)){
        echo $number1;
    }else{
        echo 'không hợp lệ';
    }

## Kiểu dữ liệu Mảng trong PHP

    $carArr = ['honda', 'toyota', 'mazda', 'vinfast', null];

    echo '<pre>'; // mảng sắp xếp từ trên xuống dưới
    print_r($carArr );
    echo '</pre>'; // mảng sắp xếp từ trên xuống dưới

-     ví dụ

  ***

      $carArr = [
          'honda',
          'name' => 'toyota',
          10 => 'mazda', // index => giá_trị
          'vinfast', // index này lấy theo index cao nhất cộng 1
          null];

      $carArr2 = [
          'honda',
          'toyota',
          'mazda', // index => giá_trị
          'vinfast', // index này lấy theo index cao nhất cộng 1
      ]; // đây là mảng tuần tự từ 0 -> ++


          //thêm phần tử vào mảng
      $carArr[14] = 'Hyundai';
      $carArr['name'] = 'Cadillac';
      // sửa giá trị của mảng
      $carArr['name'] = 'Volkswagen';   // trùng key thì sửa , khác key thì thêm mới

      // xóa phần tử mảng
      unset($carArr[14]);

      echo '<pre>'; // mảng sắp xếp từ trên xuống dưới
      print_r($carArr );
      echo '</pre>'; // mảng sắp xếp từ trên xuống dưới

      // đọc mảng tuần tự (index tăng dần từ 0)
      for($i=0; $i < count($carArr2); $i++){
          echo $carArr2[$i].'</br>';
      }
      // đọc mảng bất kì
      foreach($carArr as $key=>$car){
          echo $key.' => ';
          echo $car.'</br>';
      }

## mảng - mảng đa chiều

    // trước khi duyệt mảng
    // 1. kiểm tra biến tồn tại
    // 2. kiểm tra biến là mảng (is_array());
    // 3. kiểm tra mảng có phần tử
    // 1 và 3 dùng empty()
    $arr = 'tuanflute';
    if(!empty($arr) && is_array($arr)){
        foreach($arr as $item){
            echo $item;
        }
    }else{
        echo 'mảng không hợp lệ';
    }

- mảng đa chiều

      <!-- // khai báo mảng đa chiều có dữ liệu -->
      $arr = [
          [
              "name"=>"tfl",
              "age"=>18,
              "address"=>"ha noi"
          ],
          [
              "name"=>"hahah",
              "age"=>20,
              "address"=>"ha nam"
          ],
          [
              "name"=>"hahahahaha",
              "age"=>19,
              "address"=>"bac ninh"
          ],
      ];

      // khai báo mảng đa chiều k dữ liệu => dùng cách này nhiều vì dữ liệu sẽ dc nhập vào

      $arr = [];
      // thêm mới phần  tử mảng đa chiều
      $arr[] = [
          "name"=>"tfl",
          "age"=>18,
          "address"=>"ha noi"
      ];
      $arr[] = [
      "name"=>"hahah",
      "age"=>20,
      "address"=>"ha nam"

  ];
  $arr[][] = [
  "name"=>"công phượng",
  ];
  $arr[2][] = [
  "email"=>"congphuong@gmail.com",
  ];
  $arr['special'] = [
  "name"=>"quang hải",
  "email"=>"quanghai@gmail.com",
  ];
  $arr['special']['position'] = [
  "ceo",
  "leader",
  "manager"
  ];
  $arr[][][][] = [
  "email"=>"congphuong@gmail.com",
  ];

      //xóa mảng đa chiều

      unset($arr[2]);

// xoá phần tử cấp 3

    $lastIndex = count($arr['special']['position'])-1;
    unset($arr['special']['position'][$lastIndex]);
    echo '<pre>';
    print_r($arr);
    echo '</pre>';

---

     echo '<h1>duyet mang da chieu</h1>'; // duyệt mảng đa chiều

---

    if(!empty($arr) && is_array($arr)){
        foreach($arr as $item){
            if(is_array($item)){
            if(!empty($item)){
                echo '<h3>thong tin khach hang</h3>';
                foreach($item as $subArr){
                    if(is_array($subArr)){
                        if(!empty($subArr)){
                            echo 'cong viec : </br>';
                            foreach($subArr as $position){
                                // echo $position.'</br>';
                            }
                        }
                    }else{
                        echo $subArr.'</br>';
                    }
                }
                echo '<hr>';
            }
            }else{
                echo $item.'</br>';
            }
        }
    }

## Kiểu dữ liệu Number trong PHP

    Kiểm tra kiểu số: is_numeric($ten_bien) hoặc filter_var0)
    Kiểm tra kiểu số nguyên: is_int(Sten_bien) hoặc is_integer(Sten_bien)
    Kiểm tra kiểu số thực: is_float(Sten_bien)

    Ép kiểu số nguyên: (int)$ten_bien

    Ép kiểu số thực: (float)$ten_bien

    Lấy trị tuyệt đối: abs(Sten_bien)

    Làm tròn: round($ten_bien, $so_phan_thap_phan)

    Làm tròn xuống: floor(Sten_bien)

    Làm tròn lên: ceil(Šten_bien)

    Lấy số ngẫu nhiên: rand() hoặc rand(min, max)

    Định dạng số: number_format($ten_bien)

ví dụ

    <?php
    // is_numeric() kiểm tra xem có phải số không
    $number = '18.67899,27534785683';
    $number = str_replace('.','', $number);
    $number = str_replace(',','', $number);
    $number = (float)$number;

    echo $number;
    // kiểm tra kiểu số
    if (filter_var($number, FILTER_VALIDATE_INT)!== false) {
        echo("Biến là số nguyên");
    } else {
        echo("Biến không là số nguyên");
    }
    

    // kiểm tra kiểu số
    if(is_numeric($number)){
        echo 'day la kieu so';
    }else{
        echo 'day khong phai la kieu so';
    }
    echo '</br>';
    // echo 'tong = '.($number + 2000);

    $int = 10000000.2;
    // định dạng số
    echo number_format($int);
    echo '</br>';


    // lấy số ngẫu nhiên
    echo '</br>';
    $ran = rand(); // cách 1
    $ran = rand(0, 99); // cách 2
    echo $ran;

## Xử lý DateTime trong PHP

    https://www.php.net/manual/en/ref.datetime.php  

## Phương thức GET trong PHP

    // query string username=tuna&email=tuna@gmail.com

    echo '<pre>';
    print_r($_GET);
    // sửa tên với get
    $_GET['username'] = 'tuanflute';
    echo '</pre>';

    if(isset($_GET['username'])){
        $username = $_GET['username'];
    }
    if(isset($_GET['email'])){
        $email = $_GET['email'];
    }

    echo 'Username: '.$username.'</br>';
    echo 'Email: '.$email.'</br>';

ví dụ 2

    $data = [
        'tin tức', 
        'sản phẩm'
    ];
    foreach($data as $item){
        $url = $item;
        $url = '?module='.urlencode($url);
        echo '<a href="'.$url.'">'.$item."</br>".'</a>';
    }
    if(!empty($_GET['module'])){
        $module = urldecode($_GET['module']);
        echo $module;
    }
    echo '</br>';

    // các hàm khác 
    echo '<pre>';
    print_r($_SERVER);
    echo '</pre>';

## Phương thức POST trong PHP
- Phương thức POST dùng để gửi dữ liệu


        // echo '<pre>';
        // print_r($_POST);
        // echo '</pre>';
        if(isset($_POST['submit'])){
            $username = $_POST['username'];
            $email = $_POST['email'];

            echo 'Username: '.$username.'</br>';
            echo 'email: '.$email.'</br>';
        }
        if(isset($_POST['login'])){
            $username = $_POST['username'];
            $password = $_POST['password'];

            echo 'Username: '.$username.'</br>';
            echo 'password: '.$password.'</br>';
        }


        <form method="post" action="">
        <p>
            <input type='text' name="username" placeholder="Username..."/>
        </p>
        <p>
            <input type='text' name="email" placeholder="Email..."/>
        </p>
        <p>
            <button type="submit" name="submit">submit</button>
        </p>
        </form>
        <form method="post" action="">
        <p>
            <input type='text' name="username" placeholder="Username..."/>
        </p>
        <p>
            <input type='text' name="password" placeholder="password..."/>
        </p>
        <p>
            <button type="submit" name="login">login</button>
        </p>
        </form>


## Validate Form trong PHP

    require_once 'function.php';
        // username -> phải nhập, lớn hơn 5 kí tự
        // email -> phải nhập, định dangj email
        // age -> phải nhập, là số nguyên dương

        // print_r($_SERVER['REQUEST_METHOD'] == 'POST');
        if($_SERVER['REQUEST_METHOD'] == 'POST'){
            // khai báo mảng error để chứa  lỗi
            $errors = [];
            // validate username
            if(empty($_POST['username'])){
                $errors['username']['required'] = 'username không được bỏ trống';
            }else {
                // Trường 'username' có giá trị
                if(strlen(trim($_POST['username']))<5){
                    $errors['username']['min'] = 'username phải lớn hơn 5 kí tự';
                }
            }
            // validate email
            if(empty($_POST['email'])){
                $errors['email']['required'] = 'email không được bỏ trống';
            }else {
                // Trường 'email' có giá trị
                if(!filter_var(trim($_POST['email']), FILTER_VALIDATE_EMAIL)){
                    $errors['email']['invaild'] = 'email không hợp lệ !';
                }
            }
            // validate age
            if(empty($_POST['age'])){
                $errors['age']['required'] = 'age không được bỏ trống';
            }else {
                // Trường 'age' có giá trị
                if(!filter_var(trim($_POST['age']), FILTER_VALIDATE_INT, [
                    'options' => ['min_range'=>1]
                ])){
                    $errors['age']['invaild'] = 'age không hợp lệ !';
                }
            }
        }

        if(empty($errors)){
            redirect('list.php?message=1');
        }else{
            echo 'validate không thành công';
        }

    ?>
    <form method="post" action="">
    <p>
        <input type='text' name="username" placeholder="Username..."/> </br>
        <?php 
        echo (!empty($errors['username']['required'])) ? '<span style="color: red;">'.$errors['username']['required'].'</span>' : false;

        echo (!empty($errors['username']['min'])) ? '<span style="color: red;">'.$errors['username']['min'].'</span>':false;
        ?>
        
    </p>
    <p>
        <input type='text' name="email" placeholder="Email..."/></br>
        <?php 
        echo (!empty($errors['email']['required'])) ? '<span style="color: red;">'.$errors['email']['required'].'</span>' : false;

        echo (!empty($errors['email']['invaild'])) ? '<span style="color: red;">'.$errors['email']['invaild'].'</span>':false;
        ?>
    </p>
    <p>
        <input type='text' name="age" placeholder="Age..."/></br>
        <?php 
        echo (!empty($errors['age']['required'])) ? '<span style="color: red;">'.$errors['age']['required'].'</span>' : false;

        echo (!empty($errors['age']['invaild'])) ? '<span style="color: red;">'.$errors['age']['invaild'].'</span>':false;
        ?>
    </p>
    <p>
        <button type="submit" name="submit">submit</button>
    </p>
    </form>

function.php

    $messageArr = [
        1 => 'thêm mới thành công',
        2 => 'sưa thành công',
        3 => 'xóa thành công'
    ];
    function redirect($path){
        header("Location: $path");
        exit;
    }

    function get_mesage($code){
        global $messageArr;
        if(array_key_exists($code, $messageArr)){
            return $messageArr[$code];
        }
        return false;
    }

    function makeChecked($id){
        if(!empty($_GET['sothich'])){
            $sothich = $_GET['sothich'];
        }else{
            $sothich = [];
        }

        if(!empty($_POST['sothich']) && in_array($id, $_POST['sothich'])){
            $checked = 'checked';
        }else if(!empty($sothich) && in_array($id, $sothich)){
            $checked = 'checked';
        }else{
            $checked = false;
        }

        return $checked;
    }

list.php

    <?php
        require_once 'function.php';
    ?>

    <h3>danh sách</h3>
    <?php 
        if(!empty($_GET['message'])){
            $messageCode = $_GET['message'];
            echo get_mesage($messageCode);
        }
    ?>

checkbox.php

    require_once('function.php');
        if($_SERVER['REQUEST_METHOD'] == 'POST'){
            if(!empty($_POST['sothich'])){
                $sothich  = $_POST['sothich'];
                foreach($sothich as $item){
                    echo $item.'</br>';
                }
            }
        }

    if(!empty($_GET['sothich'])){
        $sothich = $_GET['sothich'];
    }else{
        $sothich = [];
    }

    //code checked $_get, $_post
    ?>
    <!-- <?php echo (!empty($_POST['sothich']) && in_array(2, $_POST['sothich']))?'checked':false ?> -->
    <form method="post">
        <p>sở thích</p>
        <p>
            <input type="checkbox" name="sothich[]" value="1" <?php echo makeChecked(1); ?> /> đá bóng
        </p>
        <p>
            <input type="checkbox" name="sothich[]" value="2"<?php echo makeChecked(2); ?>/>cầu lông
        </p>
        <p>
            <input type="checkbox" name="sothich[]" value="3" <?php echo makeChecked(3); ?>/>bơi
        </p>

        <p>
        <input type="checkbox" name="sothich[]" value="4" <?php echo makeChecked(4); ?>>so thich 4
        </p>
        <button type="submit">submit</button>
    </form>