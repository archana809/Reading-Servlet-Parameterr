# Reading-Servlet-Parameterr
Advance java Activivty

Reading Servlet Parameter: 
HTML Form (index.html) 
This form collects a user's name and age and sends the data to the servlet using the POST 
method. 
<!DOCTYPE html> 
<html lang="en"> 
<head> 
<meta charset="UTF-8"> 
<title>User Information Form</title> 
</head> 
<body> 
<h2>User Information</h2> 
<form action="UserInfoServlet" method="POST"> 
<label for="name">Name:</label> 
<input type="text" id="name" name="name" required><br><br> 
<label for="age">Age:</label> 
<input type="number" id="age" name="age" required><br><br> 
<input type="submit" value="Submit"> 
</form> 
</body> 
</html> 

Servlet Code (UserInfoServlet.java) 
This servlet processes the form data and displays the user's name and age. 
import java.io.*; 
import javax.servlet.*; 
import javax.servlet.http.*; 
public class UserInfoServlet extends HttpServlet { 
protected void doPost(HttpServletRequest request, HttpServletResponse response) 
throws ServletException, IOException { 
// Set the response content type 
response.setContentType("text/html"); 
// Get the PrintWriter object to send the response 
PrintWriter out = response.getWriter(); 
// Retrieve the parameters from the request 
String name = request.getParameter("name"); 
String age = request.getParameter("age"); 
// Generate the HTML response 
out.println("<html><body>"); 
out.println("<h2>User Information</h2>"); 
out.println("<p>Name: " + name + "</p>"); 
out.println("<p>Age: " + age + "</p>"); 
out.println("</body></html>"); 
} 
} 
Web Deployment Descriptor (web.xml) 
This XML configuration maps the servlet to a URL pattern. 
Xml 
<web-app xmlns="http://java.sun.com/xml/ns/j2ee" 
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
xsi:schemaLocation="http://java.sun.com/xml/ns/j2ee 
http://java.sun.com/xml/ns/j2ee/web-app_2_4.xsd" 
version="2.4"> 
<servlet> 
<servlet-name>UserInfoServlet</servlet-name> 
<servlet-class>UserInfoServlet</servlet-class> 
</servlet> 
<servlet-mapping> 
<servlet-name>UserInfoServlet</servlet-name> 
<url-pattern>/UserInfoServlet</url-pattern> 
</servlet-mapping> 
</web-app> 
