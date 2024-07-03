# document jsp_servlet

download eclipse  -> https://www.eclipse.org/downloads/

download jdk      -> https://www.oracle.com/java/technologies/downloads/

download maven    -> https://maven.apache.org/download.cgi

download tomcat   -> https://tomcat.apache.org/download-90.cgi

***hướng dẫn cài đặt***

> https://laptrinhjavaweb.com/huong-dan-cai-dat-phan-mem-4


# tạo project jsp_servlet
File->new->maven project -> create simple project -> group_id: dduooiwweb.tenwweb (vn.tuanflute) -> artifact_id là tên project -> version để mặc định (1.0) -> packing chọn war -> finish

# cấu hình pom.xml (maven)

    <properties>
		<jsp.api.version>2.0</jsp.api.version>
		<jstl.version>1.2</jstl.version>
		<servlet.api.version>3.1.0</servlet.api.version>
		<mysql.version>8.0.13</mysql.version>
	</properties>


	<dependencies>
		<!-- https://mvnrepository.com/artifact/javax.servlet/jsp-api -->
		<dependency>
			<groupId>javax.servlet</groupId>
			<artifactId>jsp-api</artifactId>
			<version>${jsp.api.version}</version>
		</dependency>
		<!-- https://mvnrepository.com/artifact/javax.servlet/javax.servlet-api -->
		<dependency>
			<groupId>javax.servlet</groupId>
			<artifactId>javax.servlet-api</artifactId>
			<version>${servlet.api.version}</version>
			<scope>provided</scope>
		</dependency>
		<dependency>
			<groupId>mysql</groupId>
			<artifactId>mysql-connector-java</artifactId>
			<version>${mysql.version}</version>
		</dependency>

	</dependencies>

 
    <properties> 
        định nghĩa các thuộc tính ở đây

        ví dụ như

        <jstl.version>1.2</jstl.version>

        jstl.version là tên tự định nghĩa và có thể sử dụng nhiều chỗ 

    </properties>



    <dependencies>
    các thư viện sẽ được khai báo ở đây 
    ví dụ import thư viện mysql để tương tác với csdl như sau

    <dependency>
			<groupId>mysql</groupId>
			<artifactId>mysql-connector-java</artifactId>
			<version>${mysql.version}</version>
		</dependency>

    </dependencies>


## cấu hình WEB-INF TRONG webapp
    <welcome-file-list>
		<welcome-file>index.jsp</welcome-file>
	</welcome-file-list>

> redirect về trang index.jsp -> là trang chủ

 **hoặc sử dụng jstl để redirect và nhiều thứ khác**

## controller

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		RequestDispatcher rd = request.getRequestDispatcher("/view/web/home.jsp");
		rd.forward(request, response);
	}

> import thư viện nhanh -> bôi đen - ctrl+shift+m -> enter

> RequestDispatcher là một interface, việc thực hiện xác định một đối tượng có thể gửi yêu cầu tới bất kỳ tài nguyên nào   (như HTML, Image, JSP, Servlet) trên server.

## start serve 
b1: nhấn tab serve -> chọn apache tomcat 

b2: show into local terminal -> terminal

b3: mvn clean insatll (build project và có file war)

b4:debug as -> debug on serve -> chọn apache tomcat ->finish

# dựng master layout
https://mvnrepository.com/artifact/opensymphony/sitemesh/2.4.2

> sử dụng sitemesh để làm việc này

tạo file decorators.xml trong WEB-INF

    <?xml version="1.0" encoding="UTF-8"?>
        <decorators defaultdir="/decorators">
        <!-- Any urls that are excluded will never be decorated by Sitemesh -->
        <excludes>
            <pattern>/api*</pattern>
        </excludes>
        
        <!-- apply Sitemesh default template -->
        <decorator name="admin" page="admin.jsp">
            <pattern>/admin*</pattern>
        </decorator>
        
        <decorator name="web" page="web.jsp">
            <pattern>/*</pattern>
        </decorator>
        
        <decorator name="login" page="login.jsp">
            <pattern>/dang-nhap</pattern>
        </decorator>
    </decorators>

-> đoạn code này giúp mình làm master layout

-> đoạn code trong  <excludes> nó sẽ không apply giao diện

-> /api*  ==> * nghĩa là bất kì thứ gì cũng dc

# ctrl + shift + u => để xóa các thứ còn thừa