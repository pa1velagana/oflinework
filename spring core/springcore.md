### :camel: Spring Core examples
---

#### Task1: Write a Car class which has an Engine, Brakes, Gear classes as a dependencies which can be injected by using constructor, setter and field
```
public class Car {
    private Engine engine;
    private Brakes brakes;
    private Gear gear;

    // Constructor injection
    public Car(Engine engine, Brakes brakes, Gear gear) {
        this.engine = engine;
        this.brakes = brakes;
        this.gear = gear;
    }

    // Setter injection
    public void setEngine(Engine engine) {
        this.engine = engine;
    }

    public void setBrakes(Brakes brakes) {
        this.brakes = brakes;
    }

    public void setGear(Gear gear) {
        this.gear = gear;
    }

    // Field injection
    @Autowired
    private Engine engine;

    @Autowired
    private Brakes brakes;

    @Autowired
    private Gear gear;

    // Other methods
    public void start() {
        engine.start();
    }

    public void stop() {
        brakes.apply();
        engine.stop();
    }

    public void changeGear(int gearNumber) {
        gear.changeGear(gearNumber);
    }
}

```
_In this implementation, the Car class has three dependencies: Engine, Brakes, and Gear. These dependencies can be injected using constructor injection, setter injection, or field injection, as demonstrated in the code. The class also has some basic methods to start the car, stop the car, and change gears_
---

#### Task2: Create a new instance of Mobile using @Bean and @Configuration annotations and print the value of the instance variable like mobileType which is passed as a constructor argument.
```
@Configuration
public class MobileConfig {

    @Bean
    public Mobile mobile() {
        return new Mobile("smartphone");
    }

    public static void main(String[] args) {
        AnnotationConfigApplicationContext context = new AnnotationConfigApplicationContext(MobileConfig.class);

        Mobile mobile = context.getBean(Mobile.class);
        System.out.println(mobile.getMobileType());

        context.close();
    }
}

public class Mobile {
    private String mobileType;

    public Mobile(String mobileType) {
        this.mobileType = mobileType;
    }

    public String getMobileType() {
        return mobileType;
    }

    public void setMobileType(String mobileType) {
        this.mobileType = mobileType;
    }
}

```
_In this implementation, we create a new configuration class MobileConfig that declares a @Bean method called mobile which returns a new instance of the Mobile class with the argument "smartphone" passed to its constructor. We then create a new AnnotationConfigApplicationContext and pass in the MobileConfig class to create a new Spring context. Finally, we get the Mobile bean from the context and print out the value of the mobileType instance variable. When you run this code, it should print "smartphone" to the console_
---
	
#### Task3: Take a Bank Class with BankName (String) and Address(Class) as instance variables and show Address autowired by Name , Type and Constructor

#### Task4: Take a School Class and show all the 3 ways of creating Movie bean a. using xml config b. using @Bean and @Configuration c. Using @Component

#### Task5: Write a Movie class showing before and after initialization using MovieBeanPostProcessor by implementing BeanPostProcessor Interface

#### Task6: Write a Password class and create a temporary password and destroy the password once permanent password is set up - using @PostConstruct and @PreDestroy annotations

#### Task7: Write a Software Class and show the life cycle methods of Software Bean by implementing Initializing Bean and Disposable Bean interfaces

#### Task8: Write a Coffeshop Class and add 2 branch Address bean definitions in xml file for Hyderabad and Secunderabad and use a Qualifier annotation to pick each Address

#### Task9: Write a Bike Class and create beans with singleton and prototype scopes

#### Task10: Write an example program for @Value annotation used for injecting property values into Television Class (with name as property)
