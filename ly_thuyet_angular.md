## cài đặt môi trường

      bước 1: npm i angular -g
      bước 2: npm i -g @angular/cli @angular/core
      bước 3: tạo project angular bằng câu lệnh trong cmd của máy
        -- ng new tên_dự_án
        --ví dụ: ng new project_angular
      bước 4: di chuyển vào file project_angular bằng câu lệnh cd project_angular
      bước 5: mở file bằng câu lệnh : ng serve --open hoặc npm start

---
    npm i angular -g
    npm i -g @angular/cli @angular/core
    ng new ten_du_an
    cd ten_du_an
    ng serve --open || npm start

## extension visual code cho angular 
     Angular Extension Pack

## Component là gì ?
- tạo component: ng generate component tên_component viết tắt : ng g c tên

**ví dụ:** 

    ng g c Home

- component dc coi như một khối như div vậy nhưng nó dc viết riêng lẻ ra
để sử dựng ta chỉ cần đưa khối div này vào

- vào thư mục home vừa tạo tìm tới file ts chính k có spec

- thấy phần selector có tên app-home 

- vậy app-home ở đây sẽ dc coi như 1 div

- để sử dụng ta chèn như sau <app-home></app-home> 

- như vậy là dùng dc r

>ở đây ta chèn vào file app.component.html

## Build - Deploy- Xây dựng và ra sản phẩm lên GitHub và Web riêng

    step1: ng build

## Module - Mô-đun là gì ?

 - là tập hợp các component vào một chỗ 

  **ví dụ**
  
   các component về user thì 1 module riêng, các component về admin thì 1 module riêng

  ---> nó sẽ xử lí khi là user thì chỉ hiển thị component về uservaf ngược lại

## bootStrap angular

    npm install bootstrap --save
    npm install jquery --save
    npm install popper.js --save

Sau khi chạy thành công lệnh trên, bạn hãy import nó vào file *angular.json*


```
"styles": [
    "node_modules/bootstrap/dist/css/bootstrap.min.css",
    "src/styles.css"
],
"scripts": [
    "node_modules/jquery/dist/jquery.min.js",
    "node_modules/bootstrap/dist/js/bootstrap.min.js"
]
```

> sử dụng bootstrap được rồi

## material

>link : https://material.angular.io/guide/getting-started

1. ng add @angular/material
2. import library
3. css, ts -->copy
4. npm start

**ví dụ**
import { MatSlideToggleModule } from '@angular/material/slide-toggle';

## Data Binding - Value - Kết nối giá trị từ code ra HTML

để kết nối dữ liệu từ file ts ra html thì trong file html ta dùng dấu {{tên_biến_trong_ts}}

ví dụ: trong file html:

  `<h2>chào bạn {{name}}</h2>`

trong file ts

 `public name = 'tuna';`

---

## Data Binding - Value - Kết nối giá trị từ code ra HTML vào thẻ Input ...

**cách1**: cơ bản vẫn dùng dấu {{tên_biến}} để trong giá trị của value

**cách 2**

    <input type="text" [value]="name" name="" id="">

>đóng ngoặc vuông value và giá trị vẫn là biến trong ts

**cách3**

    <input type="text" [value]="name" title="'đây là' + name" name="" id="">

>dùng pp cộng chuỗi để ngoặc vuông value hoặc ngoặc xoắn tên biến đều dc

## Data Binding - \*ngIf

### câu lệnh ngIf

 giống như là if bthg của ngôn ngữ khác nhưng cách viết k giống viết thẳng vào html 
---> có thể kết hợp nhiều dk như: 

     <div *ngIf="age <div 18 && name ='tuan'">hi</div>

**_ví dụ_**

    <h2 *ngIf="age < 18">bạn rất trẻ</h2>
    <h2 *ngIf="age > 18">bạn đã già</h2>

## Events binding - ngModel - Two-way binding - Liên kết 2 chiều

    <button (click)="resetName()">Reset Tên</button>

- bắt sự kiện trong thẻ html như bthg và khởi tạo function trong file ts của nó 
  
- hiển thị từ ts - html

    `<input type="text" [(ngModel)]="name" >`

- thêm ngModel như trên để lấy dữ liệu từ html - ts - html
- khi thêm ngModel vào sẽ lỗi ta cần import thư viện from vào file app.model

    import { FormsModule } from '@angular/forms'; 

-  thêm vào cả import phía dưới

 `imports: [
    BrowserModule,
    AppRoutingModule,
    FormsModule
],`

**ví dụ**

        nhập kí tự: <input type="text" [(ngModel)]= "name">
        <br>
        <h2>Tôi tên là : <span class="text-success">{{ name }}</span></h2>
    ts
    name = ''

## Template reference variable

        nhập kí tự: <input type="text" [(ngModel)]= "name" #txtName>
        <br>
        <code>my json === {{ txtName.value | json}}</code>

## directive

--> đưa ra các chỉ dẫn để angular chuyển đổi template thành dom
--> có 3 loại:
1.component --> directve với 1 template
2.attribute directve -> thay đổi việc hiển thị hoặc hành vi của các dom , component hoặc directive khác 3. structural directve --> thường thêm bớt các dom

## Style binding và class binding

--> ví dụ
=> style binding

    nhập kí tự: <input type="text" [(ngModel)]= "name" #txtName>
    <br>
    <h2 [style.color]="name.length % 2 == 0 ? 'red' : 'black'" [style.fontSize]="name.length % 2 == 0 ? '40px' : '20px'"> your name is : {{name}}</h2>

==> class bingding

    <div [class]="isHighLight ? 'circle':'square'" ></div>
    <div [class.circle]="!isHighLight" [class.square]="isHighLight"></div>

ts

    isHighLight = false
    css
    .circle{
    width: 40px;height: 40px;
    border-radius: 50%;
    background: green;
    }
    .square{
    width: 40px;height: 40px;
    border-radius: 2px;
    background: green;
    }

## để tránh trg hợp viết nhiều style như trên ta dùng [ngStyle]

ví dụ:html

    nhập kí tự: <input type="text" [(ngModel)]= "name" #txtName>
    <br>
    <h2 [ngStyle]="name.length % 2==0 ? evenStyle : oddStyle"> your name is : {{name}}</h2>

ts

    evenStyle = {color: 'red', fontSize: '20px'}
    oddStyle = {color: 'black', fontSize: '40px'}
    name = ''

## câu lệnh [ngClass]

      <td><span [ngClass]="{'red':item.hagia<=0}">{{item.hagia}}</span></td>

> [ngClass]="{'thuộc tính css':dkien}"

ví dụ:

    <div [ngClass]={circle:true}></div>

## \*ngIf

html

    <input type="text" (keyup)="changeAge($event)">
    <h3 *ngIf="age>18">ban da gia</h3>
    <h3 *ngIf="age<=18">ban rat tre</h3>

ts

    age = 20
    public changeAge(event: any){
    this.age = event.target.value
    }

## ng-template - Viết if then else trong HTML

    <input type="text" [(ngModel)]="age">
    <h3>Tuổi của bạn là {{age}}</h3>
     <div *ngIf='age <= 18; then tre; else gia'></div>
    <ng-template #tre><h2>bạn rất trẻ</h2></ng-template>
     <ng-template #gia><h2>bạn đã già</h2></ng-template>

-->dùng if then này sẽ tạo dk cho cả một khối luôn chứ k phải là từng dòng như \*ngIF ở trên
-->ví dụ với user và admin áp dụng cái này khi là user thì hiển thị component về user và ngược lại

## Data Binding - \*ngFor - Viết vòng lặp trong HTML

        <div *ngFor="let item of traicay, let i = index">
            <li>{{i+1}}.{{item}}</li>
        </div>

ts
traicay = ['tao', 'xoai', 'nho']

---

# trong file ts khai báo mảng traicay: public traicay = ['táo', 'nho', 'xoai']

trong html dùng *ngFor để loop mảng traicay

    *ngFor="let item of traicay, let i = index"
--->hiển thị dữ liệu ra bằng dấu {{}}

## ngFor với mảng đối tượng

    <div *ngFor="let item of arrWords">
    <h4 [ngStyle]="{color: item.memorized ? 'red' : 'green'}">{{item.en}}</h4>
    <p>{{item.vn}}</p>
    </div>

ts

    arrWords = [
    {id:1, en:'action', vn:'hành động', memorized: true},
    {id:1, en:'actor', vn:'diễn viên', memorized: false},
    {id:1, en:'activity', vn:'hoạt động', memorized:true},
    ]

## Thêm phần tử vào mảng kết hợp ngFor và Ẩn hiện form

        <div *ngIf="isShowForm">
        <input type="text" placeholder="english" [(ngModel)]="newEn">
        <input type="text" placeholder="vietnamese" [(ngModel)]="newVn">
        <br>
        <button (click)="addWord()">Thêm từ mới</button>
        </div>
        <button (click)="isShowForm=true" *ngIf="!isShowForm">Thêm từ mới</button>

        <select [(ngModel)]="filterStatus" style="margin-top: 50px;">
        <option value="XEM_TAT_CA">xem tất cả</option>
        <option value="XEM_DA_NHO">xem từ đã nhớ</option>
        <option value="XEM_CHUA_NHO">xem từ chưa nhớ</option>
        </select>

        <div *ngFor="let item of arrWords">
        <div class="word"
            *ngIf="getShowStatus(item.memorized)">
            <h4 [ngStyle]="{color: item.memorized ? 'red' : 'green'}">{{item.en}}</h4>
            <p [ngStyle]="{color: item.memorized ? 'blue' : 'orange'}">{{item.vn}}</p>
            <button (click)="removeWord(item.id);" style="margin-right: 10px;">delete</button>
            <button (click)="item.memorized = !item.memorized">
            {{ item.memorized ? 'chưa thuộc':'đã thuộc' }}
            </button>
        </div>
        </div>

ts
newEn = '';
newVn = '';
filterStatus = 'XEM_TAT_CA';
isShowForm = true
arrWords = [
{ id: 1, en: 'action', vn: 'hành động', memorized: true },
{ id: 1, en: 'actor', vn: 'diễn viên', memorized: false },
{ id: 1, en: 'activity', vn: 'hoạt động', memorized: true },
];

    addWord() {
        this.arrWords.push({
        id: this.arrWords.length + 1,
        en: this.newEn,
        vn: this.newVn,
        memorized: false
        });
        this.newEn = ''
        this.newVn = ''
        this.isShowForm = false
    }
    removeWord(id: number){
        const index = this.arrWords.findIndex(word => word.id === id )
        this.arrWords.splice(index, 1)
    }

    hoặc

     removeWord(id: number){
    this.arrWords = this.arrWords.filter(item => item.id != id)
    }

        getShowStatus(memorized: boolean){
        const dkXemTatCa = this.filterStatus === 'XEM_TAT_CA';
        const dkXemDaNho = this.filterStatus === 'XEM_DA_NHO' && memorized;
        const dkXemChuaNho = this.filterStatus === 'XEM_CHUA_NHO' && !memorized;

        return dkXemTatCa || dkXemDaNho || dkXemChuaNho
    }

## Tái sử dụng component và có thể đổi dữ liệu

html

    <h2>{{name}}</h2>
    <p>{{age}}</p>

ts

    import { Component, Input } from '@angular/core';
    export class HomeComponent {
        @Input() name?:String;
        @Input() age?:String;
    }

su dung component

    <app-home name="tunanana" age="18"></app-home>
    <app-home name="yeahaha" age="20"></app-home>

## ngFor kết hợp Input

    <div *ngFor="let item of arrPeople">
    <app-home [name]="item.name" [age]="item.age"></app-home>
    </div>

-->ng-container --> ẩn thẻ bao bên ngoài

    <ng-container *ngFor="let item of arrPeople">
    <app-home [name]="item.name" [age]="item.age"></app-home>
    </ng-container>

## Ouput có tham số => parent-child

child.ts

    import { Component, EventEmitter, Output } from "@angular/core";
    @Component({
    selector: 'app-child',
    template: `

        <button (click)="addForParent()">ADD</button>
        <button (click)="subForParent()">SUB</button>
        `
        })

        export class childComponent {
        @Output() myClick = new EventEmitter<boolean>();
        addForParent(){
            this.myClick.emit(true);
        }
        subForParent(){
            this.myClick.emit(false);
        }
        }

parent.ts

    import { Component } from "@angular/core";
    @Component({
    selector: 'app-parent',
    template: `

            <h3>{{ value }}</h3>
            <app-child (myClick)="changeValue($event)"></app-child>
        `
        })

        export class parentComponent {
        value = 0;
        changeValue(isAdd: boolean){
            if(isAdd){
            this.value++;
            }else{
            this.value--;
            }
        }
        }

## => child-parent

parent.ts

        import { Component, ViewChild } from "@angular/core";
        import { childComponent } from "./child-component";
        @Component({
        selector: 'app-parent',
        template: `
            <button (click)="onAddForChild()">Add For Child</button>
            <app-child></app-child>
        `
        })

        export class parentComponent {
        @ViewChild(childComponent) myChild:any;

        onAddForChild(){
            this.myChild.value++
        }
        }

child.ts

    import { Component} from "@angular/core";
    @Component({
    selector: 'app-child',
    template: `
    <h3>{{value}}</h3>
    `
    })

    export class childComponent {
    value = 0
    }

## ngContent

--> giúp tái sử dụng
--> ví dụ:

        import { Component } from "@angular/core";
        @Component({
        selector: 'app-card',
        template: `
        <div class="card">
            <div class="header">
            <ng-content select=".card-header"></ng-content>
            </div>
            <div class="body">
            <ng-content select=".card-body"></ng-content>
            </div>
        </div>
        `,
        styles:[
            `
            .card{
                padding:5px;
                margin:5px;
                background:#fff;
                border-radius:2px;
                display:inline-block;
                width: 300px;
                box-shadow: 0 10px 20px rgba(0, 0,0,0.19), 0 6px 6px rgba(0, 0, 0, 0.23)
            }
            `
        ]
        })

        export class cardComponent {

        }

html
--> nó chuyền đúng phần select

    <app-card>
    <h2 class="card-header">tuan flute</h2>
    <p class="card-body">275</p>
    </app-card>

## Pipe - Định dạng dữ liệu trong HTML. Cách dùng + viết Pipe riêng

--các hàm có sẵn hoặc mình tự viết riêng
currency:'USD':'symbol':'1.2' ==> thêm kí hiệu tiền symbol: lấy bn số thập phân
--các hàm như uppercase, lowercase, number ->ép về số, currency:'USD':'symbol':'1.2'
===>cách dùng như sau

    <td>{{item.ten | uppercase | gì gì đó..}}</td>

-->sau mỗi chỗ muốn dùng pipe thì viết sau dấu | có thể viết nhiều pipe 1 lúc dc

**cách tạo pipe**
ng generate pipe tên_pipe
----> ví dụ ng g p roundNum

ts

    import {Pipe, PipeTransform} from '@angular/core';

    @Pipe({name:'roundNum'})

    export class RoundPipe implements PipeTransform{
    transform(value: number) {
        return aMth.round(value);
    }
    }

html

    <p>{{1.75 | roundNum}}</p>

## [ngSwitch] -- \*ngSwitchCase

    <ul [ngSwitch]="loginName">
    <li *ngSwitchCase="'admin'">
        <p>admin login...</p>
    </li>
    <li *ngSwitchCase="'user'">
        <p>user login...</p>
    </li>
    <li *ngSwitchDefault>
        <p>please choose login name</p>
    </li>
    </ul>

ts
loginName = 'admin'

## directive

-->ng g d Ten_directive

---

--> ví dụ:ng g d directives/highlight

ví dụ:

---

    export class HighLightDirective {
    @Input('appHighLight') appHighLight = 'blue';

    constructor(private el: ElementRef) { }

    ngOnInit(): void {
        this.el.nativeElement.style.color = this.appHighLight;
    }
    }

html

    <p appHighLight style="width: 200px">about works!</p>
    <p [appHighLight]="myColor">about works!</p>
    <p [appHighLight]="'orange'">about works!</p>

## Services -- tạo ra các chức năng sẵn

--> như là tạp hóa vậy cần gì thì import services vào và sử dụng

--> ng g s services/common

ví dụ

common.ts

    import { Injectable } from '@angular/core';

    @Injectable({
    providedIn: 'root',
    })
    export class CommonService {
    public counter = 0;

    constructor() {}

    public binhPhuong(n: number): number {
        return n * n;
    }

    public getCounter(): number {
        return this.counter;
    }

    public setCounter(n: number): void {
        this.counter = n;
    }

public submitData(data: any):void{
console.log('gửi data lên server: ', data);

}
}

ts.sử dụng

    export class AboutComponent implements OnInit {
    public counter = 0;
    public counterBinhPhuong = 0;

    constructor(private common: CommonService) { }

    ngOnInit(): void {
        this.counter = this.common.counter;
        this.counterBinhPhuong = this.common.binhPhuong(this.counter);
        this.common.counter++;
    }
    }

## Template Driven Form

html

    <form action="" (ngSubmit)="submitForm()">
    <input type="text" [(ngModel)]="name" [ngModelOptions]="{standalone: true}" placeholder="enter your name">
    <br>
    </form>

ts

    export class FormComponent {
    name = ''
    password = ''
    constructor(private common: CommonService){}
    submitForm(){
        this.common.submitData(this.name)
        this.name = ''
        this.password = ''
    }
    }

service

import { Injectable } from '@angular/core';

    @Injectable({
    providedIn: 'root'
    })
    export class CommonService {

    constructor() { }

    public submitData(data: any):void{
        console.log('gửi data lên server: ', data);
    }
    }

## Reactive Form

html

    <form [formGroup]="formData" (ngSubmit)="onSubmit()">
    name: <input type="text" formControlName="name">
    <div *ngIf="!formData.controls.name.valid" style="color: red;">Name is require!</div>
    <br>
    age: <input type="text" formControlName="age">
    <div *ngIf="!formData.controls.age.valid" style="color: red;">Age is require!</div>

    <br>
    <button type="submit" [disabled]="!formData.valid">submit</button>
    </form>

ts

    export class ReactiveFormComponent {
    public formData = this.formBuilder.group({
        name: ['', Validators.required],
        age:['', Validators.required]
    })
    constructor(private common:CommonService, private formBuilder: FormBuilder){}
    public onSubmit():void{
        console.log('submit from: name = ' + this.formData);
        this.common.submitData(this.formData.value)

    }
    }

service

    import { Injectable } from '@angular/core';

    @Injectable({
    providedIn: 'root',
    })
    export class CommonService {
    constructor() {}

    public submitData(data: any):void{
        console.log('gửi data lên server: ', data);
    }
    }

## http

**ví dụ 1**

services

    import { HttpHeaders, HttpClient } from '@angular/common/http';
    import { Injectable } from '@angular/core';
    import { Observable } from 'rxjs';

    @Injectable({
    providedIn: 'root'
    })
    export default class HttpServiceService {
    private REST_API_SERVER = 'http://localhost:3000';
    private httpOptions = {
        headers: new HttpHeaders({
        'Content-Type': 'application/json',
        //token
        })
    }
    constructor(private HttpClient: HttpClient) { }

    public getComents(): Observable<any> {
        const url = `${this.REST_API_SERVER}/comments`;
        return this.HttpClient.get(url, this.httpOptions);
    }
    }

ts.sử dụng

    export class GetPageComponent implements OnInit{
    constructor(private httpService: HttpServiceService) { }

    ngOnInit(): void {
        this.httpService.getComents().subscribe(data=>{
            console.log('data',data);
        })
    }
    }

**ví dụ 2**

services

    import { HttpHeaders, HttpClient } from '@angular/common/http';
    import { Injectable } from '@angular/core';
    import { Observable } from 'rxjs';

    @Injectable({
    providedIn: 'root'
    })
    export default class HttpServiceService {
    private REST_2 = 'https://randomuser.me/api/?results=';
    private httpOptions = {
        headers: new HttpHeaders({
        'Content-Type': 'application/json',
        //token
        })
    }
    constructor(private HttpClient: HttpClient) { }
    public getRandomUser(user: number = 1):Observable<any>{
        const url = `${this.REST_2}` + user
        return this.HttpClient.get(url, this.httpOptions)
    }
    }

ts.sử dụng

    import { Component, OnInit } from '@angular/core';
    import HttpServiceService from '../services/http-service.service';

    @Component({
    selector: 'app-get-page',
    templateUrl: './get-page.component.html',
    styleUrls: ['./get-page.component.scss']
    })
    export class GetPageComponent implements OnInit{
    constructor(private httpService: HttpServiceService) { }

    ngOnInit(): void {
        this.httpService.getRandomUser(5).subscribe(data=>{
            console.log('dataUser', data);
        })
    }
    }

## post http

**ví dụ 3**
ts.sử dụng

        import { Component, OnInit } from '@angular/core';
        import HttpServiceService from '../services/http-service.service';

        @Component({
        selector: 'app-post-data',
        templateUrl: './post-data.component.html',
        styleUrls: ['./post-data.component.scss']
        })
        export class PostDataComponent implements OnInit{
        constructor(private HttpService: HttpServiceService) { }
        ngOnInit() {
            const payload =  {"body":"some comment 3", "postId":3}
            this.HttpService.postComents(payload).subscribe(data=>{
            console.log('postComment:', data);
            })
        }
        }

services

    import { HttpHeaders, HttpClient } from '@angular/common/http';
    import { Injectable } from '@angular/core';
    import { Observable } from 'rxjs';

    @Injectable({
    providedIn: 'root'
    })
    export default class HttpServiceService {
    private REST_2 = 'https://randomuser.me/api/?results=';
    private httpOptions = {
        headers: new HttpHeaders({
        'Content-Type': 'application/json',
        //token
        })
    }
    constructor(private HttpClient: HttpClient) { }
    public postComents(payload: any): Observable<any> {
        const url = `${this.REST_API_SERVER}/comments`;
        return this.HttpClient.post(url,payload, this.httpOptions);
    }
    }

## Cascading ComboBox. Viết danh sách chọn tỉnh/thành rồi quận/huyện

ví dụ :
html

    <div class="border-custom">
        Tỉnh/Thành Phố
    <select id="city" style="margin-right: 20px;" (change)="changeCity($event)">
        <option *ngFor="let data of vietnamData" value="{{data.city}}">{{data.city}}</option>
    </select>
        Quận/Huyện
    <select name="" id="district" >
        <option *ngFor="let ds of districts" value="{{ds}}">{{ds}}</option>
    </select>
    </div>

ts
public vietnamData = [
{ city: 'Chọn thành phố', district: ['Quận Huyện'] },
{
city: 'An Giang',
district: [
'Thành phố Long Xuyên',
'Thành phố Châu Đốc',
'Thị xã Tân Châu',
'Huyện An Phú',
'Huyện Châu Phú',
'Huyện Châu Thành',
'Huyện Chợ Mới',
'Huyện Phú Tân',
'Huyện Thoại Sơn',
'Huyện Tịnh Biên',
'Huyện Tri Tôn',
],
},
{
city: 'Bà Rịa - Vũng Tàu',
district: [
'Thành phố Vũng Tàu',
'Thị xã Bà Rịa',
'Thị xã Phú Mỹ',
'Huyện Châu Đức',
'Huyện Côn Đảo',
'Huyện Đất Đỏ',
'Huyện Long Điền',
'Huyện Tân Thành',
'Huyện Xuyên Mộc',
],
},
{
city: 'Bạc Liêu',
district: [
'Thành phố Bạc Liêu',
'Huyện Đông Hải',
'Huyện Giá Rai',
'Huyện Hòa Bình',
'Huyện Hồng Dân',
'Huyện Phước Long',
'Huyện Vĩnh Lợi',
],
},
{
city: 'Bắc Kạn',
district: [
'Thị xã Bắc Kạn',
'Huyện Ba Bể',
'Huyện Bạch Thông',
'Huyện Chợ Đồn',
'Huyện Chợ Mới',
'Huyện Na Rì',
'Huyện Ngân Sơn',
'Huyện Pác Nặm',
],
},
];

constructor() { }

public ngOnInit(): void {
console.log('vietnamData = ', this.vietnamData);
}

public changeCity(event: any): void {
const city = event.target.value;
if (!city) {
return;
}

## qr-code angular

npm i angular2-qrcode
> link :https://www.npmjs.com/package/angular2-qrcode

    <qr-code [value]="'All QR Code data goes here!'" [size]="150"></qr-code> 

**ví dụ:**

html

    <input type="text" placeholder="nhap ma qr" (keyup)="change($event)">
        <br>
        <qr-code [value]="qrInfo" [size]="size"></qr-code>

ts

    export class AppComponent {
        title = 'THEORY_ANGULAR';
        size = 200;
        qrInfo = ''
        public change(event: any){
        this.qrInfo = event.target.value
        }
    }