# PLP-Python-Object_Oriented_Programming-week-five-assignment
#Assignment 1: Design Your Own Class! 🏗️
#Create a class representing anything you like (a Smartphone, Book, or even a Superhero!).
#Add attributes and methods to bring the class to life!
#Use constructors to initialize each object with unique values.
#Add an inheritance layer to explore polymorphism or encapsulation.

# Base class for all types of phones
class Smartphone:
    def __init__(self, brand, model, battery, os):
        self.brand = brand
        self.model = model
        self.battery = battery
        self.os = os
    
    def make_call(self, number):
        print(f"{self.brand} {self.model} is calling {number}...")

    def send_message(self, number, message):
        print(f"Sending message to {number}: {message}")

    def charge(self):
        print(f"Charging {self.brand} {self.model}... Current battery: {self.battery}%")
        self.battery = 100  # Assuming charging to full
        print("Battery fully charged!")

    def show_info(self):
        print(f"Smartphone Info: {self.brand} {self.model}")
        print(f"Operating System: {self.os}")
        print(f"Battery: {self.battery}%")

# Subclass for a BasicPhone (limited features)
class BasicPhone(Smartphone):
    def __init__(self, brand, model, battery):
        # BasicPhone doesn't have an OS
        super().__init__(brand, model, battery, os="NokiaOS")
    
    def make_call(self, number):
        print(f"Basic Phone {self.brand} {self.model} is calling {number}...")

    # Basic phones typically don't support messaging
    def send_message(self, number, message):
        print("Sorry, no messaging on this BasicPhone.")

    # Overriding the charge method to include a simple battery display
    def charge(self):
        print(f"Charging BasicPhone {self.brand} {self.model}...")
        self.battery = 100
        print(f"BasicPhone battery fully charged to {self.battery}%.")

# Subclass for a SmartPhone (with extra features)
class SmartPhone(Smartphone):
    def __init__(self, brand, model, battery, os, camera_quality):
        # SmartPhone has extra camera quality attribute
        super().__init__(brand, model, battery, os)
        self.camera_quality = camera_quality
    
    def make_call(self, number):
        print(f"SmartPhone {self.brand} {self.model} is calling {number} via VoLTE...")

    def take_picture(self):
        print(f"Taking a picture with {self.camera_quality} quality camera...")

    # Overriding the charge method to show more advanced charging message
    def charge(self):
        print(f"Charging SmartPhone {self.brand} {self.model} via fast charger...")
        self.battery = 100
        print(f"SmartPhone battery fully charged to {self.battery}%.")

    def show_info(self):
        super().show_info()
        print(f"Camera Quality: {self.camera_quality} MP")

# Example usage
basic_phone = BasicPhone("Nokia", "3310", 50)
smartphone = SmartPhone("Apple", "iPhone 14", 80, "iOS", 12)

basic_phone.show_info()
basic_phone.make_call("123-456-7890")
basic_phone.send_message("123-456-7890", "Hello there!")
basic_phone.charge()

print("\n")

smartphone.show_info()
smartphone.make_call("987-654-3210")
smartphone.take_picture()
smartphone.charge()

Activity 2: Polymorphism Challenge! 🎭

Create a program that includes animals or vehicles with the same action (like move()). However, make each class define move() differently (for example, Car.move() prints "Driving" 🚗, while Plane.move() prints "Flying" ✈️).
# Base class for vehicles
class Vehicle:
    def move(self):
        raise NotImplementedError("Subclasses must implement this method.")

# Car class
class Car(Vehicle):
    def move(self):
        print("Driving 🚗")

# Plane class
class Plane(Vehicle):
    def move(self):
        print("Flying ✈️")

# Bird class
class Bird(Vehicle):
    def move(self):
        print("Flying (flapping wings) 🕊️")

# Example usage demonstrating polymorphism
def test_move(vehicle):
    vehicle.move()

# Create objects of different types
car = Car()
plane = Plane()
bird = Bird()

# Test the move() method for each vehicle
test_move(car)    # Should print: "Driving 🚗"
test_move(plane)  # Should print: "Flying ✈️"
test_move(bird)   # Should print: "Flying (flapping wings) 🕊️"
