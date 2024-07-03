# Dart Languge
IDE Dart online: https://dartpad.dev/?

IDE Flutter online: https://flutlab.io/editor/18c04bcd-79ad-4969-a4e2-a3a10f142a9c

## Khai báo biến

    void main() {
    int? a;
    print(a.runtimeType);
    print(a);
    
    int b = 10;
    print(b.runtimeType);
    print(b);
    
    double c = 7.5;
    print(c.runtimeType);
    print(c);
    
    String str = "10";
    print(str.runtimeType);
    print(str);
    
    double dbvalue = double.parse(str);
    print(dbvalue.runtimeType);
    print(dbvalue);
  }

## Phân biệt kiểu dữ liệu động: var & dynamic

**dynamic**

    dynamic e = "hello dynamic";
    print(e.runtimeType);
    print(e);
    
    e = 10;
    print(e.runtimeType);
    print(e);
    
    e = "Test";
    print(e.runtimeType);
    print(e);

  **var**

    var d;
    //var d = 27;
    print(d.runtimeType);
    print(d);
    
    d = 10;
    print(d.runtimeType);
    print(d);
    
    d = "Test";
    print(d.runtimeType);
    print(d);

> dynamic có thể gán kiểu dữ liệu nào cũng được, kể cả khi đã khởi tạo dữ liệu ban đầu
> đvs var khi khởi tạo dữ liệu ban đầu thì k thể gán với kiểu khác đã khởi tạo

## Cấu trúc dữ liệu: Enum, Iterable trong ngôn ngữ Dart

**ví dụ 1**

    enum Person {tin , hoa , sinh}


    void main() {

    print(Person.tin.name);
    print(Person.values.length);
    print(Person.values[0]);
    print(Person.values.first);
    print(Person.values.isEmpty);
    print(Person.values.isNotEmpty); // check k rỗng hay k
    
    // forrach
    Person.values.forEach((i) {
      //print(i);
      print(i.name);
    });
    
    var name = Person.tin;
    switch(name){
      case Person.tin:
        print("Tin coder");
        break;
      case Person.hoa:
        print("Hoa coder");
        break;
      case Person.sinh:
        print("Sinh coder");
        break;
      default: 
        print("Defalut");
        }
      }

**ví dụ 2**

var numbers = Iterable.generate(10);

    void main() {
    // for i
    for(int i = 0; i < numbers.length; i++) {
      print(i);
    }
    
    // for in
    for(int number in numbers){
      print(number);
        }
    }

## List trong ngôn ngữ Dart

    var list1 = [];
    List<int> numbers = [];

    void main() {
    
    // kiểm tra số phần tử
    //print(list1.length);
    //print(numbers.length);
    
    // thêm phần tử
    //list1.add(1);
    //list1.add(2);
    //list1.add(3);
    
    // duyệt danh sách
    //list1.forEach((i) {
    //  print(i.runtimeType);
    // print(i);
    //});

    
    // vi du ====================================
    
    
    //   numbers.add(3);
    //   numbers.add(4);
    //   numbers.add(5); 
    //   numbers.add(6);
        
    //   print(numbers.length);
    //   print(numbers.first);
    //   print(numbers.last);
    //   print(numbers[0]);
    //   print(numbers.isEmpty);
    
    //example

    numbers.add(3);
    numbers.add(4);
    numbers.add(5); 
    numbers.add(6);
    
    // thêm mới 1 
      list1.add(1);
    // thêm mới tất cả mảng numbers
      list1.addAll(numbers);
    
    //chèn phần tử số 10 vào vị trí số 2
      //list1.insert(2, 10);
    
    // xóa phần tử theo giá trị
        //list1.remove(10);
    // xóa phần tử theo index
        //list1.removeAt(0);
    // xóa phần tử vị trí cuối cùng
          //list1.removeLast();
    // xóa từ index 0 đến index 2 và còn lại số 5
          //list1.removeRange(0, 2);
    // xóa tất cả
        //list1.clear();
    
    list1.forEach((i){
      print(i);
    });
    
    // in đảo ngược với  reversed
    //list1.reversed.forEach((i){
      //print(i);
    //});
    }

## Maps trong ngôn ngữ Dart

    var map1 = {};
    var map2 = {"id": 1, "name": "pro 1"};
    var map3 = {"id3": 2, "name": "pro 2"};

    void main() {
        // kiểm tra phần tử mảng
        //print(map1.length);
        //print(map2.length);
        
        // duyệt mảng
    //   map2.forEach((key, value){
    //     print('$key - $value');
    //   });
        
        // thêm phần tử 
        map1['number1'] = '1';
        
        map1.addAll(map2);
        map1.addAll(map3);
        
        // xóa 1 phần tử
        map1.remove('id3');
        
        
        map1.forEach((key, value){
        print('$key - $value');
        });
        

        // xóa tất cả
    //   map1.clear();
    //   print(map1.length);
        
        // tìm kiếm
        bool check = map1.containsKey("id");
        print(check);
    }

## Sets trong ngôn ngữ Dart

    Set<int> numbers = {1, 2, 3};
    Set<int> list1 = {3, 4, 5};
    Set<String> string1 = {"tin", "hoa", "sinh"};
    Set<dynamic> test = {1, "tin", 3};

    void main() {
    
    // kiểm tra số phần tử
    //print(list1.length);
    //print(numbers.length);
    
    // thêm phần tử
    //list1.add(1);
    //list1.add(2);
    //list1.add(3);
    
    // duyệt danh sách
    //list1.forEach((i) {
    //  print(i.runtimeType);
    // print(i);
    //});

    
    // vi du ====================================
    
    
    //   numbers.add(3);
    //   numbers.add(4);
    //   numbers.add(5); 
    //   numbers.add(6);
        
    //   print(numbers.length);
    //   print(numbers.first);
    //   print(numbers.last);
    //   print(numbers[0]);
    //   print(numbers.isEmpty);
    
    //example

    numbers.add(3);
    numbers.add(4);
    numbers.add(5); 
    numbers.add(6);
    
    // thêm mới 1 
      list1.add(1);
    // thêm mới tất cả mảng numbers
      list1.addAll(numbers);
    
    //chèn phần tử số 10 vào vị trí số 2
      //list1.insert(2, 10);
    
    // xóa phần tử theo giá trị
        //list1.remove(10);
    // xóa phần tử theo index
        //list1.removeAt(0);
    // xóa phần tử vị trí cuối cùng
          //list1.removeLast();
    // xóa từ index 0 đến index 2 và còn lại số 5
          //list1.removeRange(0, 2);
    // xóa tất cả
        //list1.clear();
    
    list1.forEach((i){
      print(i);
    });
    
    // in đảo ngược với  reversed
    //list1.reversed.forEach((i){
      //print(i);
    //});
    }

## Các toán tử cơ bản quan trọng trong ngôn ngữ Dart

    // +, -, *, /, %, +=, -=,*=, /=, ==, ||, !, &&

    int a = 5;
    print(a.abs());
    // kiểm tra xem có phải int hay không 
    print(a is int); 
    // kiểm tra xem k phải string hay k
     print(a is! String);

# Các biểu thức và ký hiệu đặc biệt trong ngôn ngữ Dart

    conditon ? expr1 : expr2  ---- toán tử 3 ngôi
    ?? --- khử null
    (..) cascades ------ numbers..add(1)..add(2)..add(3);
    =>  ---- numbers.foreach((number) => print(number));

# vòng lặp (Loop) trong ngôn ngữ Dart

1. for i
2. for in
3. foreach
4.  while
5. do while


## hàm (function) trong ngôn ngữ Dart

    void main() {
    void message(){
        print("Kết quả nhận được là: ");
    }
    int tinhTong(int a, int b){
        return a + b;
    }
    
    message();
    print(tinhTong(20, 5));
    }

##  Lớp đối tượng (Class) và hàm khởi tạo Constructor

  ***OOP***
  >lập trình hướng đối tượng: https://topdev.vn/blog/oop-la-gi/

## Phạm vi truy suất (public, private) và Getter & Setter

    class City {
    void showCity() {
        print('show city');
    }
    }

    class Display {
    void showDisplay() {
        print('show display');
    }
    }

    class User implements City, Display {
    int _id = 0;
    String _name = '';

    // constructor
    User(this._id, this._name);

    int get id => _id;
    set id(int value) {
        _id = value;
    }

    String get name => _name;

    set name(String value) {
        _name = value;
    }

    @override
    String toString() {
        return '$_id - $_name';
    }

    @override
    void showCity() {
        print("show city in class user");
    }

    @override
    void showDisplay() {
        print('show display in class user');
    }
    }

## Cơ chế Flutter xây dựng giao diện & Ứng dụng "Hello World" trong Flutter