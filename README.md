package testngcheck;

import java.time.Duration;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.openqa.selenium.remote.RemoteWebDriver;
import org.testng.annotations.Optional;
import org.testng.annotations.Test;

public class Parameters {
	
	RemoteWebDriver driver;
	@org.testng.annotations.Parameters ( {"mail", "password", "browser"})
@Test
	public void login(
			@Optional("lakshmiamirtha15@gmail.com") String mail,
			@Optional("@H1a2c3k4") String password,
    @Optional("chrome") String browser)
	
	
	{
	
	
		switch (browser) {
		case "chrome":
			driver = new ChromeDriver();
			break;
			case "firefox":
				driver = new FirefoxDriver();
				break;
				default:
					System.out.println("No browser was supported");
				
		}
		
		// TODO Auto-generated method stub
		//WebDriver driver = new ChromeDriver();
		driver.manage().window().maximize();
		driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(20));
		driver.get("https://www.hackerrank.com/dashboard");
		driver.findElement(By.xpath("//button[text() = 'Log In']")).click();
		driver.findElement(By.id("username")).sendKeys(mail);
		driver.findElement(By.id("password")).sendKeys(password);
		driver.findElement(By.xpath("//button[@type = 'submit']")).click();
		driver.close();
		
		

	}

}
