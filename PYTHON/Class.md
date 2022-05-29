# ----[ CLASS - PYTHON ]---- 
                
    < [../index.md] 

## CLASS EXAMPLE
```python
       * Python 2.7 - classDog(object)

     class Dog():
         def __init__(self,name,age):
               self.name = name
               self.age = age
         def sit(self):
               print(self.name + " is sitting")

         def roll_over(self):
               print(self.name + " roll over!")

my_dog = Dog('Willie',47)
my_dog.sit()
```

## ADVANCED CLASS EXAMPLE
```python
    class Person:
        count=0
        def __init__(self,name,age,height):
            self.name = name
            self.age = age
            self.height = height
            Person.count += 1

        def __del__(self):
            print("Remove person")
            Person.count -=1

        def __str__(self):
            return ("Name: {}, Age: {}, 
                    Height: {}".format(self.name,
                    self.age,self.height))

    x = Person("Chris", 18, 160)

    print(x)
    print(Person.count)

    del(x)
    print(Person.count)

    input("Press a key to Quit")
```

## MODIFYING ATTRIBUTE VALUE
```python
    class Car():
        def __init__(self,make,model,year):
            self.make = make
            self.model = model
            self.year = year
            self.odometer_reading = 0

        def read_odometer(self):
            print("This car has " +
                  str(self.odometer_reading) +
                  " miles on it")
        def update_odometer(self,mileage):
            self.odometer_reading = mileage

    my_car = Car('Renault','Captur',2016)
    my_car.odometer_reading = 1000
    # OR my_car.update_odometer(1000)
    my_car.read_odometer()
```

## INHERITANCE
```python
     class ElectricCar(Car):
         def __init__(self,make,model,year):
             super().__init__(make,model,year)

     my_tesla = ElectricCar('tesla','model S',2016)
     my_tesla.update_odometer(100)
     print(my_tesla.read_odometer())
```
          
## IMPORT CLASS FROM OTHER FILE CARCLASS.PY
```python
    from carClass import Car,ElectricCar

    my_new_car = Car('Audi', 'A4',2016)
    print(my_new_car.get_descriptive_name())
    my_new_car.odometer_reading = 23
    my_new_car.read_odometer()

    my_Tesla = ElectricCar('tesla', 'model S',2016)
    print(my_Tesla.get_descriptive_name())
    my_Tesla.battery.describe_battery()
    my_Tesla.battery.get_range()
            ```

## CARCLASS.PY
```python
    class Car():
     """ A simple attempt to represent a car """

       def __init__(self,make,model,year):
       """ Initialize all attributes to describe
           a car"""
            self.make = make
            self.model = model
            self.year = year
            self.odometer_reading = 0

       def get_descriptive_name(self):
       """ Return a neatly formated descriptive
           name """
            long_name = str(self.year) + ' ' +
            self.make + ' ' + self.model
            return long_name.title()

       def read_odometer(self):
       """ Print a statement showing car mileage """
            print("This car has " +
                  str(self.odometer_reading) +
                  " Miles on it")

       def update_odometer(self,mileage):
       """ Set the odometer reading to the given
       value. Reject the change if it attempt to
       roll the odometer back """
            if(mileage >= self.odometer_reading):
                self.odometer_reading = mileage
            else:
                print("You can't roll back 
                      the odometer")

        def increment_odometer(self,miles):
        """ Add the given amount to the odometer
        reading """
            self.odometer_reading += miles

    class Battery():
    """ A simpliest attempt to model a batery
    for electric model car """

        def __init__(self,battery_size=60):
            """Initialize the batery attributes """
            self.battery_size = battery_size

        def describe_battery(self):
        """ print a statement describring the
        batery size..."""
            print("This car has a " +
                  str(self.battery_size) +
                  "-kWH batery.")

        def get_range(self):
        """ Print a statement about the range
        this batery provide """
            if self.battery_size == 70:
                range = 240
            elif self.battery_size == 85:
                range = 270

            message = "This car can go 
                      approximately " + str(range)
            message += " miles on full charge"
            print(message)

    class ElectricCar(Car):
    """ Model aspect of a car ,specifix to
    electric vehicle """
        def __init__(self,make,model,year):
        """ Initial attributes of parent class.
        Then initialize attributes specific to
        electric Cars """
            super().__init__(make,model,year)
            self.battery = Battery()
```
