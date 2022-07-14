package org.rk.JdbctransactionApp;
public class Company
{

public static void main(String []args)
{
String seller	="insert into rk.product valuses(?,?,?,?)";

String qry="select * from rk.product where product_n=?";

String qry2= "delete from rk.product where product_n=?";

String qry3= "update rk.product set product_t = 'laptop' where product_n='hp' ";

Connection con=null;
Statement stmt=null;
PreparedStatement pstmt=null;
PreparedStatement pstmt2=null;
Savepoint sp=null;

ResultSet rs=null;


System.out.println("enter the Product Name");
Scanner sc= new Scanner(System.in);
String product_n=sc.nextLine();

System.out.println("enter the Product Type");
String product_type=sc.nextLine();

System.out.println("enter the Product Category");
String product_c=sc.nextLine();

System.out.println("enter the Product price");
double product_price=sc.nextDouble();

sc.close();

try{
class.forName("con.mysql.jdbc.Driver");
con=DriverManager.getConnection("jdbc:mysql://localhost:3306?user=root&password:root");
con.setAutoCommit(false);

pstmst1=con.preparestatement(seller);  //insert data by seller 
pstmst1.setString(1,product_n);
pstmst1.setString(2,product_type);
pstmst1.setString(3,product_c);
pstmst1.setString(4,product_price);

pstmt1.executeUpdate();
system.out.println("data executed");
con.commit();

System.out.println("enter the Product Name for searching ");  // seaching data with product name
String product_n=sc.nextLine();
pstmst1 =con.prepareStatement(qry); // for customer
pstmst1.setString(1,product_n);
rs=pstmt1.executeQuery();

if(rs.next())
{
String product_t=rs.getString(2);
String product_c=rs.getString(3);
double product_price=rs.getString(4);

System.out.println(product_t+" "product_c+" "+product_price);
}
else{
System.out.println("invalid input");
}

stmt con.CreateStatement();

System.out.println("enter the Product Name for Delete");  // deleting data with product name
String product_n=sc.nextLine();
stmt.executeUpdate(qry2);
System.out.println("data deleted")


}
catch(ClassNotFoundException| SQLException){
e.printStackTrace();
}
finally{
if(rs!=null){
try{
rs.close();
}
catch(SQLException){
e.printStackTrace();
}
}

if(pstmt1!=null){
try{
pstmt1.close();
}
catch(SQLException){
e.printStackTrace();
}
}

ifcon!=null){
try{
con.close();
}
catch(SQLException){
e.printStackTrace();
}
}
}
}
