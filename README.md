#1
public class Phone {
    private String number;
    private String model;
    private double weight;

    
    public Phone(String number, String model, double weight) {
        this.number = number;
        this.model = model;
        this.weight = weight;
    }

    public Phone(String number, String model) {
        this(number, model, 0.0);
    }

    public Phone() {
        this("", "", 0.0);
    }

    
    public String getNumber() {
        return number;
    }

    public void setNumber(String number) {
        this.number = number;
    }

    public String getModel() {
        return model;
    }

    public void setModel(String model) {
        this.model = model;
    }

    public double getWeight() {
        return weight;
    }

    public void setWeight(double weight) {
        this.weight = weight;
    }

    
    public void receiveCall(String callerName) {
        System.out.println(callerName + " is ringing");
    }

    public void receiveCall(String callerName, String callerNumber) {
        System.out.println(callerName + " is ringing from " + callerNumber);
    }

    public void sendMessage(String... phoneNumbers) {
        System.out.print("Sending message to: ");
        for (String number : phoneNumbers) {
            System.out.print(number + " ");
        }
        System.out.println();
    }

    
    public static void main(String[] args) {
        
        Phone phone1 = new Phone("123456789", "iPhone 15 PRO", 150.5);
        Phone phone2 = new Phone("987654321", "Samsung Flip 5");
        Phone phone3 = new Phone();

        
        System.out.println("Phone 1: Number - " + phone1.getNumber() + ", Model - " + phone1.getModel() + ", Weight - " + phone1.getWeight());
        System.out.println("Phone 2: Number - " + phone2.getNumber() + ", Model - " + phone2.getModel() + ", Weight - " + phone2.getWeight());
        System.out.println("Phone 3: Number - " + phone3.getNumber() + ", Model - " + phone3.getModel() + ", Weight - " + phone3.getWeight());

        
        phone1.receiveCall("Aidana");
        phone2.receiveCall("Erkezhan", "987654421");
        phone3.sendMessage("111222333", "453555726", "767848919");

        
        Phone phone4 = new Phone("776348777", "Google Pixel");
        System.out.println("Phone 4: Number - " + phone4.getNumber() + ", Model - " + phone4.getModel() + ", Weight - " + phone4.getWeight());
    }
}
#p2
public class Person {
    
    private String fullName;
    private int age;

    
    public Person() {
        
    }

    public Person(String fullName, int age) {
        this.fullName = fullName;
        this.age = age;
    }

    
    public void move() {
        System.out.println(fullName + " is moving.");
    }

    public void talk() {
        System.out.println(fullName + " is talking.");
    }

    
    public static void main(String[] args) {
        
        Person person1 = new Person();
        Person person2 = new Person("John Doe", 25);

        
        person1.move();
        person1.talk();

        person2.move();
        person2.talk();
    }
}
#3
public class Matrix {
    private double[][] data;
    private int rows;
    private int columns;

    
    public Matrix(int rows, int columns) {
        this.rows = rows;
        this.columns = columns;
        this.data = new double[rows][columns];
    }
    
    public Matrix add(Matrix otherMatrix) {
        if (this.rows != otherMatrix.rows || this.columns != otherMatrix.columns) {
            System.out.println("Matrix dimensions do not match for addition.");
            return null;
        }

        Matrix resultMatrix = new Matrix(rows, columns);
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < columns; j++) {
                resultMatrix.data[i][j] = this.data[i][j] + otherMatrix.data[i][j];
            }
        }

        return resultMatrix;
    }

    
    public Matrix multiplyByScalar(double scalar) {
        Matrix resultMatrix = new Matrix(rows, columns);
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < columns; j++) {
                resultMatrix.data[i][j] = this.data[i][j] * scalar;
            }
        }

        return resultMatrix;
    }

    
    public Matrix multiply(Matrix otherMatrix) {
        if (this.columns != otherMatrix.rows) {
            System.out.println("Matrix dimensions do not match for multiplication.");
            return null;
        }

        Matrix resultMatrix = new Matrix(this.rows, otherMatrix.columns);
        for (int i = 0; i < this.rows; i++) {
            for (int j = 0; j < otherMatrix.columns; j++) {
                for (int k = 0; k < this.columns; k++) {
                    resultMatrix.data[i][j] += this.data[i][k] * otherMatrix.data[k][j];
                }
            }
        }

        return resultMatrix;
    }

    
    public void print() {
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < columns; j++) {
                System.out.print(data[i][j] + "\t");
            }
            System.out.println();
        }
    }

    
    public static void main(String[] args) {
        Matrix matrix1 = new Matrix(2, 3);
        matrix1.data = new double[][]{{1, 2, 3}, {4, 5, 6}};

        Matrix matrix2 = new Matrix(2, 3);
        matrix2.data = new double[][]{{7, 8, 9}, {10, 11, 12}};

        System.out.println("Matrix 1:");
        matrix1.print();

        System.out.println("\nMatrix 2:");
        matrix2.print();

        Matrix sumMatrix = matrix1.add(matrix2);
        System.out.println("\nSum of Matrix 1 and Matrix 2:");
        if (sumMatrix != null) {
            sumMatrix.print();
        }

        Matrix scalarProductMatrix = matrix1.multiplyByScalar(2.5);
        System.out.println("\nMatrix 1 multiplied by scalar 2.5:");
        scalarProductMatrix.print();

        Matrix productMatrix = matrix1.multiply(matrix2);
        System.out.println("\nMatrix 1 multiplied by Matrix 2:");
        if (productMatrix != null) {
            productMatrix.print();
        }
    }
}
#4
import java.util.Arrays;


class Book {
    private String name;
    private String author;

    public Book(String name, String author) {
        this.name = name;
        this.author = author;
    }

    @Override
    public String toString() {
        return name + " by " + author;
    }
}


public class Reader {
    private String fullName;
    private int libraryCardNumber;
    private String faculty;
    private String dateOfBirth;
    private String phone;

    

    
    public void takeBook(int numBooks) {
        System.out.println(fullName + " took " + numBooks + " books");
    }

    public void takeBook(String... bookTitles) {
        System.out.print(fullName + " took books: ");
        for (String title : bookTitles) {
            System.out.print(title + ", ");
        }
        System.out.println();
    }

    public void takeBook(Book... books) {
        System.out.print(fullName + " took books: ");
        for (Book book : books) {
            System.out.print(book + ", ");
        }
        System.out.println();
    }

    
    public void returnBook(String... bookTitles) {
        System.out.print(fullName + " returned the books: ");
        for (String title : bookTitles) {
            System.out.print(title + ", ");
        }
        System.out.println();
    }

    public void returnBook(int numBooks) {
        System.out.println(fullName + " returned " + numBooks + " books");
    }

    public static void main(String[] args) {
        
        Reader reader1 = new Reader();
        reader1.setFullName("Petrov VV");
        reader1.setLibraryCardNumber(12345);
        reader1.setFaculty("Engineering");
        reader1.setDateOfBirth("01-01-1990");
        reader1.setPhone("123-456-7890");

        
        reader1.takeBook(3);
        reader1.takeBook("Adventures", "Dictionary", "Encyclopedia");
        Book book1 = new Book("Adventures", "Author1");
        Book book2 = new Book("Dictionary", "Author2");
        Book book3 = new Book("Encyclopedia", "Author3");
        reader1.takeBook(book1, book2, book3);

        
        reader1.returnBook("Adventures", "Dictionary", "Encyclopedia");
        reader1.returnBook(3);
    }
}
#5
public class RecursiveNumberPrinter {

    
    public static void printNumbers(int A, int B) {
        if (A < B) {
            
            System.out.print(A + " ");
            if (A < B) {
                printNumbers(A + 1, B);
            }
        } else if (A > B) {
            
            System.out.print(A + " ");
            if (A > B) {
                printNumbers(A - 1, B);
            }
        } else {
            
            System.out.print(A + " ");
        }
    }

    public static void main(String[] args) {
        int A = 5;
        int B = 10;

        System.out.println("Numbers from " + A + " to " + B + ":");
        printNumbers(A, B);
    }
}
#p6
class Student {
    String firstName;
    String lastName;
    String group;
    double averageMark;

    Student(String firstName, String lastName, String group, double averageMark) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.group = group;
        this.averageMark = averageMark;
    }

    
    int getScholarship() {
        return (averageMark == 5) ? 100 : 80;
    }
}

class Aspirant extends Student {
    String scientificWork;

    Aspirant(String firstName, String lastName, String group, double averageMark, String scientificWork) {
        super(firstName, lastName, group, averageMark);
        this.scientificWork = scientificWork;
    }

    
    @Override
    int getScholarship() {
        return (averageMark == 5) ? 200 : 180;
    }
}

public class Main {
    public static void main(String[] args) {
        // Creating objects of Student and Aspirant
        Student regularStudent = new Student("John", "Doe", "GroupA", 4.5);
        Aspirant postGraduate = new Aspirant("Alice", "Smith", "GroupB", 5.0, "Research on AI");
        
        
        Student[] students = {regularStudent, postGraduate};

  
        for (Student student : students) {
            System.out.println(student.firstName + " " + student.lastName +
                    " Scholarship Amount: $" + student.getScholarship());
        }
    }
}
#p7
package com.company.details;

public class Engine {
    private int power;
    private String manufacturer;

    public Engine(int power, String manufacturer) {
        this.power = power;
        this.manufacturer = manufacturer;
    }

    @Override
    public String toString() {
        return "Engine{" +
                "power=" + power +
                ", manufacturer='" + manufacturer + '\'' +
                '}';
    }
}
package com.company.professions;

public class Person {
    private String fullName;
    private int drivingExperience;

    public Person(String fullName, int drivingExperience) {
        this.fullName = fullName;
        this.drivingExperience = drivingExperience;
    }

    @Override
    public String toString() {
        return "Person{" +
                "fullName='" + fullName + '\'' +
                ", drivingExperience=" + drivingExperience +
                '}';
    }
}
[14:45, 07.12.2023] Аяука ☀️: package com.company.vehicles;

import com.company.details.Engine;
import com.company.professions.Person;

public class Car {
    private String brand;
    private String carClass;
    private int weight;
    private Person driver;
    private Engine motor;

    public Car(String brand, String carClass, int weight, Person driver, Engine motor) {
        this.brand = brand;
        this.carClass = carClass;
        this.weight = weight;
        this.driver = driver;
        this.motor = motor;
    }

    public void start() {
        System.out.println("Let's go");
    }

    public void stop() {
        System.out.println("Let's stop");
    }

    public void turnRight() {
        System.out.println("Turn right");
    }

    public void turnLeft() {
        S…
[14:45, 07.12.2023] Аяука ☀️: package com.company.vehicles;

public class Lorry extends Car {
    private int carryingCapacity;

    public Lorry(String brand, String carClass, int weight, Person driver, Engine motor, int carryingCapacity) {
        super(brand, carClass, weight, driver, motor);
        this.carryingCapacity = carryingCapacity;
    }

    public int getCarryingCapacity() {
        return carryingCapacity;
    }

    @Override
    public String toString() {
        return "Lorry{" +
                "carryingCapacity=" + carryingCapacity +
                "} " + super.toString();
    }
}
package com.company.vehicles;

public class SportCar extends Car {
    private int topSpeed;

    public SportCar(String brand, String carClass, int weight, Person driver, Engine motor, int topSpeed) {
        super(brand, carClass, weight, driver, motor);
        this.topSpeed = topSpeed;
    }

    public int getTopSpeed() {
        return topSpeed;
    }

    @Override
    public String toString() {
        return "SportCar{" +
                "topSpeed=" + topSpeed +
                "} " + super.toString();
    }
}
#p8 
class Animal {
    String food;
    String location;

    public Animal(String food, String location) {
        this.food = food;
        this.location = location;
    }

    public void makeNoise() {
        System.out.println("Such an animal is sleeping");
    }

    public void eat() {
        System.out.println("The animal is eating " + food);
    }

    public void sleep() {
        System.out.println("The animal is sleeping");
    }
}

class Dog extends Animal {
    String breed;

    public Dog(String food, String location, String breed) {
        super(food, location);
        this.breed = breed;
    }

    @Override
    public void makeNoise() {
        System.out.println("The dog is barking");
    }

    @Override
    public void eat() {
        System.out.println("The dog is eating " + food);
    }
}

class Cat extends Animal {
    String color;

    public Cat(String food, String location, String color) {
        super(food, location);
        this.color = color;
    }

    @Override
    public void makeNoise() {
        System.out.println("The cat is meowing");
    }

    @Override
    public void eat() {
        System.out.println("The cat is eating " + food);
    }
}

class Horse extends Animal {
    String maneColor;

    public Horse(String food, String location, String maneColor) {
        super(food, location);
        this.maneColor = maneColor;
    }

    @Override
    public void makeNoise() {
        System.out.println("The horse is neighing");
    }

    @Override
    public void eat() {
        System.out.println("The horse is eating " + food);
    }
}

class Veterinary {
    public void treatAnimal(Animal animal) {
        System.out.println("Food: " + animal.food + ", Location: " + animal.location);
    }
}

public class Main {
    public static void main(String[] args) {
        Animal[] animals = {
                new Dog("Bones", "Yard", "Labrador"),
                new Cat("Fish", "Living Room", "Tabby"),
                new Horse("Hay", "Stable", "Brown")
        };

        Veterinary vet = new Veterinary();

        for (Animal animal : animals) {
            vet.treatAnimal(animal);
        }
    }
}
#p2 task
import java.util.ArrayList;


interface TrainComponent {
    int getCapacity();
    int getPassengers();
}


class Train {
    private int totalCapacity; 
    private int totalPassengers;  
    private ArrayList<TrainComponent> components;  

    
    public Train() {
        totalCapacity = 0;
        totalPassengers = 0;
        components = new ArrayList<>();
    }

    
    public void addComponent(TrainComponent component) {
        components.add(component);
        totalCapacity += component.getCapacity();
        totalPassengers += component.getPassengers();
    }

    
    public int getTotalCapacity() {
        return totalCapacity;
    }

    
    public int getTotalPassengers() {
        return totalPassengers;
    }
}


class Locomotive implements TrainComponent {
    private int capacity;  
    private int passengers;  

    
    public Locomotive() {
        this.capacity = 0;
        this.passengers = 0;
    }

    
    public int getCapacity() {
        return capacity;
    }

    public int getPassengers() {
        return passengers;
    }
}


class Wagon implements TrainComponent {
    private int capacity;  
    private int passengers;  

    
    public Wagon(int capacity, int passengers) {
        this.capacity = capacity;
        this.passengers = passengers;
    }


    public int getCapacity() {
        return capacity;
    }

    public int getPassengers() {
        return passengers;
    }
}


public class Main {
    public static void main(String[] args) {
        
        Train myTrain = new Train();
        Locomotive locomotive = new Locomotive();
        Wagon passengerWagon = new Wagon(50, 30);
        Wagon cargoWagon = new Wagon(100, 0);

        
        myTrain.addComponent(locomotive);
        myTrain.addComponent(passengerWagon);
        myTrain.addComponent(cargoWagon);

        
        System.out.println("Total train capacity: " + myTrain.getTotalCapacity());
        System.out.println("Total number of passengers in the train: " + myTrain.getTotalPassengers());
    }
}
#p3 task
import java.util.List;
import java.util.ArrayList;


class Company {
    private List<Employee> employees;  

    
    public Company() {
        employees = new ArrayList<>();
    }

    
    public void addEmployee(Employee employee) {
        employees.add(employee);
    }

    
    public double calculateTotalCost() {
        double totalCost = 0;
        for (Employee employee : employees) {
            totalCost += employee.calculateSalary();  // Assuming the salary is a measure of the cost
        }
        return totalCost;
    }
}


class Employee {
    private String name;  
    private int age;  

    
    public Employee(String name, int age) {
        this.name = name;
        this.age = age;
    }

    
    public double calculateSalary() {
        return 0;  
    }
}


class Developer extends Employee {
    private double hourlyRate;  
    private int hoursWorked; 

  
    public Developer(String name, int age, double hourlyRate, int hoursWorked) {
        super(name, age);
        this.hourlyRate = hourlyRate;
        this.hoursWorked = hoursWorked;
    }

    
    @Override
    public double calculateSalary() {
        return hourlyRate * hoursWorked;  
    }
}

class Manager extends Employee {
    private double monthlySalary;  

    
    public Manager(String name, int age, double monthlySalary) {
        super(name, age);
        this.monthlySalary = monthlySalary;
    }

    
    @Override
    public double calculateSalary() {
        return monthlySalary;  
    }
}


public class Main {
    public static void main(String[] args) {
        
        Company myCompany = new Company();
        Developer john = new Developer("John", 25, 20.0, 160);
        Manager alice = new Manager("Alice", 30, 3000.0);

        
        myCompany.addEmployee(john);
        myCompany.addEmployee(alice);

        
        System.out.println("Total cost of the project: $" + myCompany.calculateTotalCost());
    }
}

#p4 task
import java.util.ArrayList;
import java.util.List;


class Aquarium {
    private List<AquaticAnimal> aquaticAnimals;  
    private List<Accessory> accessories;  

    
    public Aquarium() {
        aquaticAnimals = new ArrayList<>();
        accessories = new ArrayList<>();
    }

    
    public void addAquaticAnimal(AquaticAnimal aquaticAnimal) {
        aquaticAnimals.add(aquaticAnimal);
    }

    
    public void addAccessory(Accessory accessory) {
        accessories.add(accessory);
    }

  
    public double calculateTotalCost() {
        double totalCost = 0;

        
        for (AquaticAnimal aquaticAnimal : aquaticAnimals) {
            totalCost += aquaticAnimal.calculateCost();
        }

        
        for (Accessory accessory : accessories) {
            totalCost += accessory.getPrice();
        }

        return totalCost;
    }
}

abstract class AquaticAnimal {
    private String name;
    private double price;


    public AquaticAnimal(String name, double price) {
        this.name = name;
        this.price = price;
    }


    public abstract double calculateCost();
}


class Fish extends AquaticAnimal {
    private int size;

    
    public Fish(String name, double price, int size) {
        super(name, price);
        this.size = size;
    }

 
    @Override
    public double calculateCost() {
        return getPrice() * size;  // Cost = Price * Size
    }
}


class Reptile extends AquaticAnimal {
    private String species;

    // Constructor for initializing a reptile
    public Reptile(String name, double price, String species) {
        super(name, price);
        this.species = species;
    }

    // Override method to calculate the cost of the reptile (assume a fixed cost for reptiles)
    @Override
    public double calculateCost() {
        return getPrice();  // Cost for reptiles is their fixed price
    }
}


class Accessory {
    private String name;
    private double price;

    
    public Accessory(String name, double price) {
        this.name = name;
        this.price = price;
    }

  
    public double getPrice() {
        return price;
    }
}


public class Main {
    public static void main(String[] args) {
       
        Aquarium myAquarium = new Aquarium();
        Fish goldfish = new Fish("Goldfish", 5.0, 4);
        Reptile turtle = new Reptile("Turtle", 20.0, "Terrapene carolina");
        Accessory castleDecoration = new Accessory("Castle Decoration", 8.0);
        Accessory plantDecoration = new Accessory("Plant Decoration", 3.0);

       
        myAquarium.addAquaticAnimal(goldfish);
        myAquarium.addAquaticAnimal(turtle);
        myAquarium.addAccessory(castleDecoration);
        myAquarium.addAccessory(plantDecoration);

        
        System.out.println("Total cost of the aquarium: $" + myAquarium.calculateTotalCost());
    }
}
#p5 task
import java.util.ArrayList;
import java.util.List;


abstract class Stone {
    private String name;  
    private double weight; 
    private double pricePerCarat;  

   
    public Stone(String name, double weight, double pricePerCarat) {
        this.name = name;
        this.weight = weight;
        this.pricePerCarat = pricePerCarat;
    }

   
    public double calculateCost() {
        return weight * pricePerCarat;  
    }

    
    public String getName() {
        return name;
    }

 
    public double getWeight() {
        return weight;
    }

   
    public double getPricePerCarat() {
        return pricePerCarat;
    }
}


class PreciousStone extends Stone {
    private String gemType;  
   
    public PreciousStone(String name, double weight, double pricePerCarat, String gemType) {
        super(name, weight, pricePerCarat);
        this.gemType = gemType;
    }

   
    @Override
    public double calculateCost() {
        return super.calculateCost() * 1.5;  // Cost with a 50% premium for precious stones
    }
}


class SemiPreciousStone extends Stone {
    private String mineral;  // Mineral type of semi-precious stone (e.g., amethyst, topaz)

   
    public SemiPreciousStone(String name, double weight, double pricePerCarat, String mineral) {
        super(name, weight, pricePerCarat);
        this.mineral = mineral;
    }
}


class Necklace {
    private List<Stone> stones;  

   
    public Necklace() {
        stones = new ArrayList<>();  
    }

   
    public void addStone(Stone stone) {
        stones.add(stone); 
    }

   
    public double calculateTotalWeight() {
        return stones.stream().mapToDouble(Stone::getWeight).sum();
    }

 
    public double calculateTotalCost() {
        return stones.stream().mapToDouble(Stone::calculateCost).sum();
    }
}

public class Main {
    public static void main(String[] args) {
        
        Necklace myNecklace = new Necklace();
        PreciousStone diamond = new PreciousStone("Diamond", 2.5, 20000.0, "Diamond");
        SemiPreciousStone amethyst = new SemiPreciousStone("Amethyst", 1.8, 5000.0, "Quartz");
        SemiPreciousStone topaz = new SemiPreciousStone("Topaz", 2.0, 3000.0, "Aluminum silicate");

    
        myNecklace.addStone(diamond);
        myNecklace.addStone(amethyst);
        myNecklace.addStone(topaz);

      
        System.out.println("Total weight of the necklace: " + myNecklace.calculateTotalWeight() + " carats");
        System.out.println("Total cost of the necklace: " + myNecklace.calculateTotalCost() + " kzt");
    }
}
