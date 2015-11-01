# StudentManagementSystem
A system that can manage students' grades and message themselves

---------------10.26开发记录------------------

1. 设计footer.html用于版本声明
2. header-default为初始登录header
3. header-user为普通用户header
4. header-admin为管理员header

-------------------未完成---------------------

* user及admin中设置注销按钮，并重定向至初始页面，同时清理缓存
<%
	session.invalidate();
 	response.sendRedirect("login.jsp");
%>


-----------------10.27/28开发记录---------

1. 静态页面部署基本完成
2. 后台页面单独设计，通过admin.jsp登录
3. 设置页头导航和页尾版权声明为浮动页面

------------------------------------------

1. 添加动态代码
2. 使用javabean进行数据的传送
3. 使用insertstudentinfo.jsp实现插入数据

-----------------10.30开发记录-------------

1. 增加管理员查找页面
2. 通过session.getAttribute()以及setAttribute()
获取学生id
	表单发送数据给validatestudent.jsp，validatestudent.jsp中接收表单传来的参数
       <%
		String id = request.getParameter("id");

		
		if (studentservice.validateStudent(student)) {
			//将当前jsp页面中的student实例存储在名为student的session字段中
			session.setAttribute("student", student);
			session.setAttribute("id", id);
	%>
	<jsp:forward page="studentquerypage.jsp"></jsp:forward>
	<%
		} else {
	%>
	<jsp:forward page="index.jsp"></jsp:forward>
	<%


	<%
		String userid = (String) session.getAttribute("id");
		if (userid != null) {
			out.println(userid);
		}
	%>
3.使用EL表达式获取参数
	<font color="green">学生 <font color="red">${sessionScope.id}</font>欢迎使用在线成绩查询</font>
					</h1>
4.增加学生成绩查询页面

-----11.1------------

1.增加删除信息页面，
2. bug修复
3. 删除信息模块成功运行