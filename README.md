# EXCEPTIONSNLOGGING
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <groupId>www.prashanth</groupId>
  <artifactId>loggers</artifactId>
  <version>0.0.1-SNAPSHOT</version>
  <packaging>jar</packaging>

  <name>loggers</name>
  <url>http://maven.apache.org</url>

  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <java.version>1.8</java.version>
    <maven.compiler.source>1.8</maven.compiler.source>
    <maven.compiler.target>1.8</maven.compiler.target>
  </properties>
  <dependencies>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>3.8.1</version>
      <scope>test</scope>
    </dependency>
    <dependency>
    <!-- https://mvnrepository.com/artifact/org.apache.logging.log4j/log4j-core -->
    <groupId>org.apache.logging.log4j</groupId>
    <artifactId>log4j-core</artifactId>
    <version>2.12.1</version>
   </dependency>
   <!-- https://mvnrepository.com/artifact/org.apache.logging.log4j/log4j-api -->
  <dependency>
    <groupId>org.apache.logging.log4j</groupId>
    <artifactId>log4j-api</artifactId>
    <version>2.12.1</version>
 </dependency>
   </dependencies>
</project>
 63  src/main/java/HouseConstructionCalculator.java 
@@ -0,0 +1,63 @@
import java.util.Scanner;
import org.apache.logging.log4j.LogManager;
import org.apache.logging.log4j.Logger;
import java.io.PrintStream;
import java.io.FileDescriptor;
import java.io.FileOutputStream;
class Material
{
private static final Logger LOGGER=LogManager.getLogger(Material.class);
private static final int MaterialChoose = 0;
void totalCost()
{
double Total_cost;
Scanner sc=new Scanner(System.in);
PrintStream myoutput=new PrintStream(new FileOutputStream(FileDescriptor.out));
LOGGER.info("HOUSE CONSTRUCTION CALCULATOR \n");
myoutput.print("<<<<<<<<<<<<<<<<<<**************************>>>>>>>>>>>>>>>>>> \n");
LOGGER.info("varied requirements \n");
System.out.printf("***************************************** \n");
LOGGER.info("1.Standard material costs 1000 INR per square feet \n");
LOGGER.info("2.Above standard material costs 1300 INR per square feet\n");
LOGGER.info("3.High standard material costs 1900 INR per square feet\n");
LOGGER.info("4.High standard material with full Automated house costs 4400 INR per square feet\n");
System.out.printf("<<-------------------**********************-------------------------->> \n");
LOGGER.info("Enter your choice for ur house construction standard material\n");
int MaterialChoosen=sc.nextInt();
LOGGER.info("Enter Total Area Of House In Square Feet \n");
double TotalArea=sc.nextDouble();
if(MaterialChoosen==1)
{
Total_cost=TotalArea*1000;
 myoutput.print("Total cost of construction of house with standard material is:" +Total_cost+"INR");
}
else if(MaterialChoosen==2)
{
	  Total_cost=TotalArea*1300;
       myoutput.print("Total cost of construction of house with above standard material is:" +Total_cost+"INR");
}
else if(MaterialChoosen==3)
{
      Total_cost=TotalArea*1900;
       myoutput.print("Total cost of construction of house with high standard material is:" +Total_cost+"INR");
}
else if(MaterialChoosen==4)
{
	  Total_cost=TotalArea*4400;
       myoutput.print("Total cost of construction of house with high standard and fully automated material is:" +Total_cost+"INR");
}
else
{
	LOGGER.warn("enter a valid choice");
}
}
}

class HouseConstructionCalculator
{
public static void main(String[] args) 
{
Material material=new Material();
material.totalCost();
}
} 
 83  src/main/java/Interest.java 
@@ -0,0 +1,83 @@
import javax.swing.*;
import javax.swing.event.*;
import java.awt.event.*;
import java.awt.*;
import java.lang.Math.*;
class InterestCalculator implements ActionListener
{
JFrame frame;
JPanel panel;
JLabel principleamount,time,rateofintrest,result;
JTextField textFieldforp,textFieldfort,textFieldforrate,textFieldforresult;
JButton buttonsimpleintrest,buttoncompoundintrest;
InterestCalculator()
{
frame=new JFrame("INTEREST CALCULATOR");
frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
frame.setSize(500,500);
frame.setLayout(new GridLayout());
frame.getContentPane().setBackground(Color.GREY);
panel=new JPanel();
panel.setBackground(Color.GREEY);
principleamount=new JLabel("PRINCIPLE AMOUNT(A)");
principleamount.setSize(50,50);
panel.add(principleamount);
textFieldforp=new JTextField(10);
panel.add(textFieldforp);
time=new JLabel("TIME PERIOD(T)");
time.setSize(50,50);
panel.add(time);
textFieldfort=new JTextField(10);
panel.add(textFieldfort);
rateofinterest=new JLabel("RATE OF INTREST(R)");
rateofinterest.setSize(50,50);
panel.add(rateofintrest);
textFieldforrate=new JTextField(10);
panel.add(textFieldforrate);
result=new JLabel("INTEREST RECEIVED");
result.setSize(50,50);
panel.add(result);
textFieldforresult=new JTextField(10);
panel.add(textFieldforresult);
buttonsimpleinterest=new JButton("SIMPLE INTEREST");
buttonsimpleinterest.addActionListener(this);
buttoncompoundinterest=new JButton("COMPOUND INTEREST");
buttoncompoundinterest.addActionListener(this);
panel.add(buttonsimpleinterest);
panel.add(buttoncompoundinterest);
frame.add(panel);
frame.setVisible(true);
}
public void actionPerformed(ActionEvent ae)
{
if(ae.getSource()==buttonsimpleinterest)
{
float A=Float.parseFloat(textFieldforp.getText());
float t=Float.parseFloat(textFieldfort.getText());
float r=Float.parseFloat(textFieldforrate.getText());
float answer=((A*t*r)/100);
textFieldforresult.setText(String.valueOf(answer));
}
if(ae.getSource()==buttoncompoundintrest)
{
double p=Double.parseDouble(textFieldforp.getText());
double t=Double.parseDouble(textFieldfort.getText());
double r=Double.parseDouble(textFieldforrate.getText());
double answer=(A * (Math.pow((1 +(r/100)),t))); 
textFieldforresult.setText(String.valueOf(answer));
}
}
}
class Interest
{
public static void main(String[] args)
{
InterestCalculator interestCalculator=new InterestCalculator();
}
}






 18  src/main/resources/log4j2.properties 
@@ -0,0 +1,18 @@
rootLogger.level=DEBUG

appender.console.type=console
appender.console.name=prashanthkumar
appender.console.layout.type=PatternLayout
appender.console.layout.pattern=%d{yyyy-MM-dd HH:mm:ss} %-5p %c{1}:%L - %m%n

rootLogger.appenderRef.stdout.ref=prashanthkumar

appender.rolling.type=RollingFile
appender.rolling.name=RollingFile
appender.rolling.fileName=D:\\logs\\logging-first.log
appender.rolling.filePattern=logarchive-%d{MM-dd-yy-HH-mm-ss}-%i.log.zip
appender.rolling.layout.type=PatternLayout
appender.rolling.layout.pattern=%d{yyyy-MM-dd HH:mm:ss} %-5p %c{1}:%L - %m%n
appender.rolling.policies.type=Policies

rootLogger.appenderRef.rolling.ref=RollingFile 
 38  src/test/java/www/prashanthkumar/loggers/AppTest.java 
@@ -0,0 +1,38 @@
package www.prashanthkumar.loggers;

import junit.framework.Test;
import junit.framework.TestCase;
import junit.framework.TestSuite;

/**
 * Unit test for simple App.
 */
public class AppTest 
    extends TestCase
{
    /**
     * Create the test case
     *
     * @param testName name of the test case
     */
    public AppTest( String testName )
    {
        super( testName );
    }

    /**
     * @return the suite of tests being tested
     */
    public static Test suite()
    {
        return new TestSuite( AppTest.class );
    }

    /**
     * Rigourous Test :-)
     */
    public void testApp()
    {
        assertTrue( true );
    }
}
