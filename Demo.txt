import org.openqa.selenium.*;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;

import java.time.Duration;
import java.time.Instant;

public class BirthLogin extends Main {
    public static void main(String[] args) {
        WebDriver driver = new ChromeDriver();
        driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(30));
        driver.get("https://provider.birthmodel.com");
        driver.manage().window().maximize();
        driver.findElement(By.id("email")).sendKeys("betty@yopmail.com");
        driver.findElement(By.id("password")).sendKeys("Test@123");
        driver.findElement(By.xpath("//*[@id=\"btn-login\"]")).click();
        try {
            // Using WebDriverWait to wait for the element to be clickable
            WebElement activePatientsLink = new WebDriverWait(driver, Duration.ofSeconds(60))
                    .until(ExpectedConditions.elementToBeClickable(By.xpath("//div[@id='root']//li[contains(text(),'Active Patients')]")));

           ((JavascriptExecutor) driver).executeScript("arguments[0].scrollIntoView(true);", activePatientsLink);
            activePatientsLink.click();

        } catch (ElementClickInterceptedException e) {
            System.out.println("Exception: " + e.getMessage());
        }
        driver.findElement(By.xpath("//div[@class=\"emt-tile-flex\"]//button")).click();
        //driver.findElement(By.xpath("//div[@class=\"add-patient-popup\"]//p[contains(text(),'Add Patient via EMR System')]")).click();
        driver.findElement(By.xpath("//div[@class='add-patient-popup']//p[contains (text (), 'Add Patient Manually')]")).click();
        //driver.findElement(By.xpath("//div[@class='MuiBox-root jss106 dialog-message']//div[@class='MuiInputBase-root MuiOutlinedInput-root MuiInputBase-fullWidth MuiInputBase-formControl']//input[@class='MuiInputBase-input MuiOutlinedInput-input']")).sendKeys("202667");
        driver.findElement(By.name("firstName")).sendKeys("Charlie");
        driver.findElement(By.name("lastName")).sendKeys("Mun");
        driver.findElement(By.name("dateOfBirth")).click();
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[3]/div/div/div/div[2]/div[2]/div/div/div[2]/div[2]/div[1]/div[6]")).click();
        driver.findElement(By.name("mrn")).sendKeys("23693");
        driver.findElement(By.name("firstExamination")).click();
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[6]/div/div/div[1]/div[2]/div[2]/div/div/div[2]/div[2]/div[1]/div[6]")).click();//date
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[6]/div/div/div[2]/div[1]/span/input")).click();//year
        /*WebElement element = new WebDriverWait(driver, Duration.ofSeconds(60)).until(ExpectedConditions.elementToBeClickable(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[6]/div/div/div[2]/div[1]/span/input")));

        // Scroll to the element if needed
        ((JavascriptExecutor) driver).executeScript("arguments[0].click();", element);

        // Click on the element
        element.click();
        driver.findElement(By.xpath("//div[@class='time-field-css']//input")).click();
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[6]/div/div/div[2]/div[1]/div[2]/div/div/div/div[2]/div[2]/ul/li[21]")).click();
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[6]/div/div/div[2]/div[1]/div[2]/div/div/div/div[2]/div[3]/ul/li[2]")).click();*/
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[6]/div/div/div[2]/div[1]/div[2]/div/div/div/div[2]/div[1]/ul/li[5]")).click();//hr
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[6]/div/div/div[2]/div[1]/div[2]/div/div/div/div[2]/div[2]/ul/li[57]")).click();//min
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[6]/div/div/div[2]/div[1]/div[2]/div/div/div/div[2]/div[3]/ul/li[2]")).click();//pm
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[7]/div/div[1]/span/span[25]")).click();//time ok button
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[7]/div/div[1]/span/span[6]")).click();//dilation
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[12]/div/div/div/input")).sendKeys("25.08");//BMI
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[8]/div[1]/div/div[2]")).click();//Effacement dropdown
        driver.findElement(By.xpath("/html/body/div/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[8]/div[1]/div[2]/div/div[3]")).click();//Effacement value
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[10]/div[1]/div[1]/div[2]")).click();//Position
        driver.findElement(By.xpath("/html/body/div/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[10]/div[1]/div[2]/div/div[3]")).click();//position value
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[11]/div[1]/div/div[2]")).click();// consistency of cervix
        driver.findElement(By.xpath("/html/body/div/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[11]/div[1]/div[2]/div/div[3]")).click();// consistency value
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[13]/div[1]/div[1]/div[2]")).click();//races
        driver.findElement(By.xpath("/html/body/div/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[13]/div[1]/div[2]/div/div[7]")).click();//races value
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[9]/div/div[1]/span/span[12]")).click();
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[14]/div/div[1]/span/span[14]")).click();//prior deliveries
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[15]/div/div[1]/div[1]/div/div[1]/div/label/span[1]/span[1]/input")).click();//gestational agedriver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[15]/div/div[2]/div[1]/div/div/div/input")).sendKeys("39");
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[15]/div/div[2]/div[2]/div/div/input")).sendKeys("5");
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[15]/div/div[1]/div[1]/div/div[2]/div/label/span[1]/span[1]/input")).click();//EDD
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[15]/div/div[2]/div/div/div")).click();//date picker
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[15]/div/div[2]/div/div/div/div[2]/div[2]/div/div/div[2]/div[2]/div[5]/div[5]")).click();//date
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[17]/div/div[1]/div/div[1]/div/label/span[1]/span[1]/input")).click();//TOLAC
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[19]/div/div/div[1]/div/div[2]/div/label/span[1]/span[1]/input")).click();//CRA
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[20]/div[1]/div/div[1]/div/div[1]/div/label/span[1]/span[1]/input")).click();//Oxytocin
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[20]/div[2]/div/div/div/div[1]/div[1]/div/div/input")).click();// oxy Date
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[20]/div[2]/div/div/div/div[1]/div[2]/div[2]/div/div/div[2]/div[2]/div[3]/div[3]")).click();
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[20]/div[2]/div/div/div/div[2]/div[1]/span")).click();//time
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[20]/div[2]/div/div/div/div[2]/div[1]/div[2]/div/div/div/div[2]/div[1]/ul/li[7]")).click();//hr
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[20]/div[2]/div/div/div/div[2]/div[1]/div[2]/div/div/div/div[2]/div[2]/ul/li[57]")).click();//min
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[20]/div[2]/div/div/div/div[2]/div[1]/div[2]/div/div/div/div[2]/div[3]/ul/li[2]")).click();//pm
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[20]/div[2]/div/div/div/div[2]/div[1]/div[2]/div/div/div/div[3]/div")).click();//ok
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[25]/div/div/div/input")).sendKeys("3456");
        try {
            WebElement element = driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[26]/div[1]/div"));

            // Create Actions object
            Actions actions = new Actions(driver);

            // Move to the element and perform the click action
            actions.moveToElement(element).click().perform();
        } catch (Exception e) {
            // Handle any exceptions
            e.printStackTrace();
        }
        //driver.findElement(By.xpath("/html/body/div/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[26]/div[1]/div[1]/div[2]")).click();//assign practice
        driver.findElement(By.xpath("/html/body/div/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[26]/div[1]/div[2]/div/div/div")).click();//practice name
        driver.findElement(By.xpath("/html/body/div/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[27]/div[1]/div/div[2]")).click();//provider
        driver.findElement(By.xpath("/html/body/div/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[27]/div[1]/div[2]/div/div/div")).click();//provider name
        driver.findElement(By.xpath("//*[@id=\"root\"]/div/div[1]/div[1]/div[2]/div[5]/div[4]/div[1]/div[29]/div/button[2]")).click();//add


    }
}