# Lab 8 (IT 314)
# Name - Sanket Doshi
# ID - 202001008

### 2. Test method to test the behaviour of the Boa class :
```
import org.junit.Assert;
import org.junit.Test;
public class BoaTest {

  @Test
  public void testIsHealthy() {
    Boa healthyBoa = new Boa("Lucy", 8, "granola bars");
    Assert.assertTrue(healthyBoa.isHealthy());
   
    Boa sickBoa = new Boa("Sneaky", 6, "mice");
    Assert.assertFalse(sickBoa.isHealthy());
  }

  @Test
  public void testFitsInCage() {
    Boa smallBoa = new Boa("Tiny", 2, "rats");
    Assert.assertTrue(smallBoa.fitsInCage(5));
    Assert.assertFalse(smallBoa.fitsInCage(1));

    Boa largeBoa = new Boa("Goliath", 20, "chicken");
    Assert.assertTrue(largeBoa.fitsInCage(25));
    Assert.assertFalse(largeBoa.fitsInCage(10));
  }
}
```
In this JUnit test class, we use the @Test annotation to indicate each individual test case. The Assert class provides different methods to check expected behavior, and JUnit will automatically report any failed assertions. In the testIsHealthy() method, we create a healthy and a sick boa and use assertTrue() and assertFalse() to test their isHealthy() methods. In the testFitsInCage() method, we create a small and a large boa and use assertTrue() and assertFalse() to test their fitsInCage() methods with different cage lengths.
</br>

### 3. Modified setUp() method in the BoaTest class :
```
public class BoaTest {
    private Boa jen;
    private Boa ken;
   
    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }
   
    // write test methods here
}
```
Note that I have added private fields for jen and ken to the BoaTest class, as required by the modified setUp() method. The setUp() method now creates two Boa objects, jen and ken, which can be used by the test methods.
</br>

### 4. Modified testIsHealthy() method in the BoaTest class :
```
@Test
public void testIsHealthy() {
    // check that jen is not healthy
    assertFalse(jen.isHealthy());
   
    // check that ken is healthy
    assertTrue(ken.isHealthy());
}
```
This test method checks the behavior of the isHealthy() method in the Boa class by calling it on the jen and ken objects created in the setUp() method. We expect jen to not be healthy because her favorite food is "grapes" instead of "granola bars", and we expect ken to be healthy because his favorite food is "granola bars". The assertFalse() and assertTrue() methods are JUnit assertion methods that check that the provided condition is false and true, respectively. If either of these assertions fails, the test method will fail and JUnit will report an error.
</br>

### 5. Modified testFitsInCage() method in the BoaTest class :
```
@Test
public void testFitsInCage() {
    // Test for jen
    assertFalse(jen.fitsInCage(1)); // cage length is less than length of boa
    assertTrue(jen.fitsInCage(2)); // cage length is equal to length of boa
    assertTrue(jen.fitsInCage(3)); // cage length is greater than length of boa

    // Test for ken
    assertFalse(ken.fitsInCage(2)); // cage length is less than length of boa
    assertTrue(ken.fitsInCage(3)); // cage length is equal to length of boa
    assertTrue(ken.fitsInCage(4)); // cage length is greater than length of boa
}
```
</br>

### 7. Here's the modified Boa class with the new lengthInInches() method:
```
public class Boa {
    private String name;
    private int length; // the length of the boa, in feet
    private String favoriteFood;

    public Boa(String name, int length, String favoriteFood) {
        this.name = name;
        this.length = length;
        this.favoriteFood = favoriteFood;
    }

    // returns true if this boa constrictor is healthy
    public boolean isHealthy() {
        return this.favoriteFood.equals("granola bars");
    }

    // returns true if the length of this boa constrictor is
    // less than the given cage length
    public boolean fitsInCage(int cageLength) {
        return this.length < cageLength;
    }

    // produces the length of the Boa in inches
    public int lengthInInches() {
        return this.length * 12;
    }
}
```
### Here's an example of a new test case in the BoaTest class that tests the lengthInInches() method:
```
import static org.junit.Assert.assertEquals;
import org.junit.Before;
import org.junit.Test;

public class BoaTest {
    private Boa jen;
    private Boa ken;

    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }

    @Test
    public void testLengthInInches() {
        assertEquals(24, jen.lengthInInches());
        assertEquals(36, ken.lengthInInches());
    }
}
```
This new test case checks that the lengthInInches() method returns the expected value when called on each of the Boa objects created in the setUp() method. It uses the assertEquals() method to compare the expected value to the actual value returned by the lengthInInches() method. The @Test annotation indicates that this is a test method that should be run by JUnit.
</br>
