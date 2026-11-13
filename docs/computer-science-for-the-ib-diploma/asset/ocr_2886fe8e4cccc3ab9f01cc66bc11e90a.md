```
abstract class Shape{
    public abstract double getArea();
    public abstract double getPerimeter();
}
class Rectangle extends Shape {
    protected double width;
    protected double height;
    Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }
    @Override // Specify we are overriding the abstract method
    public double getArea() {
        return this.width * this.height;
    }
    @Override // Specify we are overriding the abstract method
    public double getPerimeter() {
        return 2 * (this.width + this.height);
    }
}
class Circle extends Shape {
    protected double radius;
    Circle(double radius) {
        this.radius = radius;
    }
    @Override
    public double getArea() {
        return Math.PI*this.radius*this.radius;
    }
    @Override
    public double getPerimeter() {
        return 2*Math.PI*this.radius;
    }
}
class Main {
    public static void main(String[] args) {
        Shape[] shapes = new Shape[4];
        shapes[0] = new Rectangle(10.0, 4.0);
        shapes[1] = new Rectangle(36.0, 7.0);
        shapes[2] = new Circle(42.0);
        shapes[3] = new Circle(10.0);
        for (int i = 0; i < shapes.length; i++) {
            System.out.println( shapes[i].getArea() );
            System.out.println( shapes[i].getPerimeter() );
        }
    }
}
```