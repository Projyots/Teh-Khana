# Teh-Khana
Optum files
package com.selenium1.practice.Sel1;

import java.util.List;
import java.util.Set;
import java.util.concurrent.TimeUnit;
import org.openqa.selenium.support.ui.Select;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.*;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;

import com.thoughtworks.selenium.webdriven.commands.GetAllWindowTitles;

import java.util.Iterator;

import bsh.org.objectweb.asm.Constants;

//public class WebECSA {

import org.openqa.selenium.WebDriver;

import org.openqa.selenium.chrome.ChromeDriver;

public class WebECSA {

	public static void main(String[] args) throws InterruptedException {

		System.setProperty("webdriver.chrome.driver",
				"C:\\Users\\psriva12\\Downloads\\chromedriver_win32\\chromedriver.exe");

		// Initialize browser
		ChromeOptions options = new ChromeOptions();
		options.setExperimentalOption("useAutomationExtension", false);
		WebDriver driver = new ChromeDriver(options);
		// WebDriver driver=new ChromeDriver();
		options.addArguments("disable-infobars");

		options.addArguments("--start-maximized");

		// Open site
		// String
		// baseUrl="http://SRAUDIT1:Feb_2014@httptst1/WEBCSA-AF/web/controller/Home.webcsa";
		driver.get("http://SRAUDIT1:Feb_2014@httptst1/WEBCSA-AF/web/controller/Home.webcsa");

		// Maximize browser

		driver.manage().window().maximize();
		options.setExperimentalOption("useAutomationExtension", false);

		// a[text()='Member']

		driver.findElement(By.xpath("//a[text()='Member']")).click();

		// It will return the parent window name as a String
		String parent = driver.getWindowHandle();

		// This will return the number of windows opened by Webdriver and will return
		// Set of St//rings
		Set<String> s1 = driver.getWindowHandles();

		// Now we will iterate using Iterator
		Iterator<String> I1 = s1.iterator();

		while (I1.hasNext()) {

			String child_window = I1.next();

			// Here we will compare if parent window is not equal to child window then we
			// will close

			if (!parent.equals(child_window)) {
				driver.switchTo().window(child_window);
				
//				List <WebElement> webEl = driver.findElements(By.tagName("frame"));
				//System.out.println(driver.findElement(By.cssSelector("frame[name='MemberInfo']")).getText());
//				driver.switchTo().frame("MEMBERallpans");
//				System.out.println(driver.switchTo().frame(0).getPageSource());
				System.out.println(driver.switchTo().window(child_window).getTitle());
				driver.manage().timeouts().implicitlyWait(15, TimeUnit.SECONDS);
				//driver.findElement(By.cssSelector("input[name='CallerId']")).sendKeys("Hellloooooooooooooo");
				driver.switchTo().frame("MEMBERallpans");
				System.out.println("Frmaes");
				driver.switchTo().defaultContent();
				System.out.println("Frmaes2");
				//Switching to sub frames from main frame
				driver.switchTo().frame("searchpan");
				//driver.switchTo().frame("wmain");
				//driver.switchTo().frame("MemberInfo");
				
				//clearing the fields on next window
				driver.findElement(By.name("callClear")).click();
				System.out.println("Checking");
				driver.switchTo().defaultContent();
				
				
				//
				
				driver.switchTo().frame("searchpan");
				
				driver.findElement(By.name("CallerId")).sendKeys("1247834201");
				System.out.println("able to get inforamtion");
				driver.findElement(By.name("callSubmit")).click();
				Thread.sleep(1500);
				
				driver.switchTo().defaultContent();
				
				System.out.println("Checking2");
				///driver.switchTo().frame("MainFrame");
				//driver.switchTo().frame("wmain");
				driver.switchTo().frame("MEMBERallpans");
				//System.out.println("Checking3");
				
				driver.switchTo().frame("wleftnav");
				
				//drop down selection 
				/*Select memberid = new Select(driver.findElement(By.xpath(".//*select[@id='CallerType']")));
				memberid.selectByVisibleText("Member ID");
				*/
				//driver.findElement(By.xpath("//a[contains(@title,'Claims Inquiry')]")).click();
				driver.findElement(By.xpath("//a[text()='Claims']")).click();
				//driver.findElement(By.xpath("a[@title='Claims Inquiry']")).click();
				System.out.println("Checking4");
				//a[@title='Claims Inquiry']
				

						
/*				String parentwindow= driver.getWindowHandle();


				Set<String> allwindows = driver.getWindowHandles();

					for(String window: allwindows)
					{
					if(!(parentwindow.equalsIgnoreCase(window)))
					{
					driver.switchTo().window(window);
*/				
				
				
				for (String winHandle : driver.getWindowHandles()) {
				    driver.switchTo().window(winHandle); // switch focus of WebDriver to the next found window handle (that's your newly opened window)
				    System.out.println(driver.switchTo().window(winHandle).getTitle());
				}
				
				
				
				System.out.println("title");
				
				
				
				
				
				
				 driver.findElement(By.xpath("//a[@href='http://httptst1/WEBCSA-EF/service/controller/medMgmt.ValidateEOB?claimNumber=7310E15404&memberCode=1247834201']")).click();
				 System.out.println("pdf");
				//driver.findElement(By.tagName("http://httptst1/WEBCSA-EF/service/controller/medMgmt.ValidateEOB?claimNumber=7244E50906&memberCode=1310943304")).click();
				
				 
				 for (String winHandle2 : driver.getWindowHandles()) {
					    driver.switchTo().window(winHandle2); // switch focus of WebDriver to the next found window handle (that's your newly opened window)
					    System.out.println(driver.switchTo().window(winHandle2).getTitle());
					}
			
				 
					
				 driver.findElement(By.xpath("//a[contains(.,'View PDF')]")).click();
				System.out.println("print EOB");
				
				
				//clickLinkByHref("http://httptst1/WEBCSA-EF/service/controller/medMgmt.ValidateEOB?claimNumber=7244E50906&memberCode=1310943304");
					
				//http://httptst1/WEBCSA-EF/service/controller/medMgmt.ValidateEOB?claimNumber=7306E22610&memberCode=1310943304
				
				
				
			}

			/*
			 * driver.findElement(By.name("membercode")).sendKeys("Test");
			 * driver.findElement(By.name("GO")).click()
			 */;

		//driver.switchTo().window(parent)
		}}}

