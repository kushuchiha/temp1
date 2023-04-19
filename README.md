# Lab-8_202001104

Name :Kush Shah
ID: 202001104


![image](https://user-images.githubusercontent.com/75687413/233025994-6f7f4cd8-7019-44d6-b872-7cf008266f1d.png)


![image](https://user-images.githubusercontent.com/75687413/233031390-182bcff5-7f0f-48eb-a4e0-802b46584804.png)


![image](https://user-images.githubusercontent.com/75687413/233031957-bb8e69d0-be18-4fd2-8902-0c320d5d95ee.png)


![image](https://user-images.githubusercontent.com/75687413/233032369-f59542f3-72af-4b5f-b3d5-a83b91a38f92.png)


Code For Boa.java

package Lab8package;

public class Boa {
	private String name;
	private int length; // the length of the boa, in feet
	private String favoriteFood;
	public Boa (String name, int length, String favoriteFood){
	this.name = name;
	this.length = length;
	this.favoriteFood = favoriteFood;
	}
	// returns true if this boa constrictor is healthy
	public boolean isHealthy(){
	return this.favoriteFood.equals("granola bars");
	}
	// returns true if the length of this boa constrictor is
	// less than the given cage length
	public boolean fitsInCage(int cageLength){
	return this.length < cageLength;
	}
	public int lengthInInches() {
		return this.length * 12;
	}
	}

Test Case code
package Lab8package;

import static org.junit.Assert.*;

import org.junit.Before;
import org.junit.Test;


public class BoaTest {

	@Test
	public void testIsHealthy() {
		Boa healthyBoa = new Boa("Healthy Boa", 5, "granola bars");
		Boa unhealthyBoa = new Boa("Unhealthy Boa", 5, "junk food");
		
		assertTrue(healthyBoa.isHealthy());
		assertFalse(unhealthyBoa.isHealthy());
	}

	@Test
	public void testFitsInCage() {
		Boa smallBoa = new Boa("Small Boa", 5, "granola bars");
		Boa largeBoa = new Boa("Large Boa", 10, "granola bars");
		
		assertTrue(smallBoa.fitsInCage(6));
		assertTrue(largeBoa.fitsInCage(12));
		
	}
	
	@Before
	public void setUp() throws Exception {
	Boa jen = new Boa("Jennifer", 2, "grapes");
	Boa ken = new Boa ("Kenneth", 3, "granola bars");
	
	assertFalse(ken.fitsInCage(2));
    assertFalse(ken.fitsInCage(3));
    assertTrue(ken.fitsInCage(5));
    
    assertFalse(jen.fitsInCage(1));
    assertFalse(jen.fitsInCage(2));
    assertTrue(jen.fitsInCage(3));
	}
	
	@Test
	public void TestLengthInInches() {
		Boa priyank = new Boa("Jennifer", 2, "grapes");
		Boa daksh = new Boa ("Kenneth", 3, "granola bars");
		
		assertEquals(23,kush.lengthInInches());
	}

}


Results for feet to inch

![image](https://user-images.githubusercontent.com/75687413/233037134-66982172-9ea2-4cbc-a55d-4172034c6d7d.png)


8.
Different annotations:
Test methods annotated with @Test will be run, but the order of the tests is not guaranteed. This means that the tests may run in any order during test execution. It's important to write tests in such a way that they are independent of each other and do not rely on a specific execution order.
Any method annotated with @Before will be run before each test executes. This allows you to set up common test fixtures or perform any necessary setup steps before each test runs. For example, you can use @Before to initialize objects, set up mock objects, or perform any other necessary setup operations.
Any method annotated with @After will be run after each test executes. This allows you to clean up any resources or perform any necessary teardown steps after each test runs. For example, you can use @After to release resources, reset state, or perform any other necessary cleanup operations.
