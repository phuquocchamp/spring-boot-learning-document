## Java Based Configuration.

### 1. Code Demo.

Vehicle.java

```java
package com.spring.JavaBasedConfiguration;

public interface Vehicle {
    public void move();
}

```

Bike.java

```java
package com.spring.JavaBasedConfiguration;

public class Bike implements Vehicle{
    @Override
    public void move() {
        System.out.println("Bike is moving !");
    }
}

```

Bicycle.java

```Java
package com.spring.JavaBasedConfiguration;

public class Bicycle implements Vehicle{
    @Override
    public void move() {
        System.out.println("Bycicle is moving !");
    }
}

```

Car.java

```java
package com.spring.JavaBasedConfiguration;

public class Car implements Vehicle {
    @Override
    public void move() {
        System.out.println("Car is moving !");
    }
}

```

Ta cài đặt 3 lớp Car, Bicycle, Bike được kế thừa từ lớp Vehicle.

Traveler.java

```java
package com.spring.JavaBasedConfiguration;

public class Traveler {
    private final Vehicle vehicle;

    public Traveler(Vehicle vehicle){
        this.vehicle = vehicle;
    }

    public void startJouney(){
        vehicle.move();
    }
}

```

AppConfig.java

```java
package com.spring.JavaBasedConfiguration;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class AppConfig {
    @Bean
    public Vehicle car(){
        return new Car();
    }
    @Bean
    public Vehicle bike(){
        return new Bike();
    }
    @Bean
    public Vehicle bicycle(){
        return new Bicycle();
    }
    @Bean
    public Traveler traveler(){
        return new Traveler(bike()); // DI
    }
}

```

Lớp Config chứa các cài đặt metadata cho ứng dụng Spring, Lớp này sẽ đóng vai trò là IoC Container quản lí các đối tượng từ được tạo ra từ các bean Car, Bike, Bicycle.

> Các khái niệm về `@Configuration` và `Bean` được nói rõ trong phần [Learning Flow](./LearningFlow.MD)

Application.java

```java
package com.spring.JavaBasedConfiguration;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class AppConfig {
    @Bean
    public Vehicle car(){
        return new Car();
    }
    @Bean
    public Vehicle bike(){
        return new Bike();
    }
    @Bean
    public Vehicle bicycle(){
        return new Bicycle();
    }
    @Bean
    public Traveler traveler(){
        return new Traveler(bike()); // DI
    }
}

```
