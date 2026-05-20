## clase consecionaria
```java
 public static void main(String[] args) {
        Persona vendedor = new Persona("Juan Pérez", "33444555","46666276");
        Persona comprador = new Persona("Ana García", "40111222","46232249");

        
        Vehiculo auto1 = new Auto(4, "Corola", "Toyota", 344566776, "AD654837");
        Vehiculo moto1 = new Moto("150", "2026", "Honda", 23457835, "M785653");

        
        Venta factura1 = new Venta(vendedor, comprador, auto1);

        System.out.println("--- Procesando Venta de Concesionaria ---");
        factura1.imprimirFactura();        
        System.out.println("\n------------------------------------------");
        
        // Registramos la venta de una Moto usando el mismo proceso
        Venta factura2 = new Venta(vendedor, comprador, moto1);
        factura2.imprimirFactura();
    }
    
}


```

## Clase Persona


```java
public class Persona {
    private String Nombre;
    private String Apellido;
    private String DNI;

    public Persona() {
    }

    public Persona(String Nombre, String Apellido, String DNI) {
        this.Nombre = Nombre;
        this.Apellido = Apellido;
        this.DNI = DNI;
    }

    public String getNombre() {
        return Nombre;
    }

    public String getApellido() {
        return Apellido;
    }

    public String getDNI() {
        return DNI;
    }

    public void setNombre(String Nombre) {
        this.Nombre = Nombre;
    }

    public void setApellido(String Apellido) {
        this.Apellido = Apellido;
    }

    public void setDNI(String DNI) {
        this.DNI = DNI;
    }
    
    
}
```
## Clase Veehiculo
```java
public abstract class Vehiculo {
   private String Modelo;
   private String Marca;
   private float Precio;
   private String Patente;

    public Vehiculo() {
    }

    public Vehiculo(String Modelo, String Marca, float Precio, String Patente) {
        this.Modelo = Modelo;
        this.Marca = Marca;
        this.Precio = Precio;
        this.Patente = Patente;
    }

    public String getModelo() {
        return Modelo;
    }

    public String getMarca() {
        return Marca;
    }

    public float getPrecio() {
        return Precio;
    }

    public String getPatente() {
        return Patente;
    }

   
   public abstract void mostrarDetalles();
}
```
## Clase Auto
```java

public class Auto extends Vehiculo{
    private int Puerta;  

    public Auto(int Puerta) {
        this.Puerta = Puerta;
    }

    public Auto(int Puerta, String Modelo, String Marca, float Precio, String Patente) {
        super(Modelo, Marca, Precio, Patente);
        this.Puerta = Puerta;
    }

    public int getPuerta() {
        return Puerta;
    }

    public void setPuerta(int Puerta) {
        this.Puerta = Puerta;
    }

    @Override
    public void mostrarDetalles() {
         System.out.println("Auto: " + super.getModelo() + "Marca: " + super.getMarca() + "| Puertas: " + Puerta + " | Precio: $" + super.getPrecio()+"Patente: "+ super.getPatente()); 
    }
    
}
```
## Clase Moto
```java
public class Moto extends Vehiculo{
    private String Cilindrada;

    public Moto(String Cilindrada) {
        this.Cilindrada = Cilindrada;
    }

    public Moto(String Cilindrada, String Modelo, String Marca, float Precio, String Patente) {
        super(Modelo, Marca, Precio, Patente);
        this.Cilindrada = Cilindrada;
    }

    public String getCilindrada() {
        return Cilindrada;
    }

    public void setCilindrada(String Cilindrada) {
        this.Cilindrada = Cilindrada;
    }

    @Override
    public void mostrarDetalles() {
        System.out.println("Auto: " + super.getModelo() + "Marca: " + super.getMarca() + "Cilindrada:"+Cilindrada+ " | Precio: $" + super.getPrecio()+"Patente: "+ super.getPatente()); 
    
}
}
```
## Clase venta
```java
public class Venta {
   private Persona vendedor;
    private Persona comprador;
    private Vehiculo vehiculo;
    private static int contadorFacturas = 0;
    private int numeroFactura;
    
    public Venta(Persona vendedor, Persona comprador, Vehiculo vehiculo) {
        this.vendedor = vendedor;
        this.comprador = comprador;
        this.vehiculo = vehiculo;
        this.numeroFactura = ++contadorFacturas;
    }
    
    public void imprimirFactura() {
        System.out.println("FACTURA N°: " + numeroFactura);
        System.out.println("----------------------");
        System.out.println("VENDEDOR: " + vendedor);
        System.out.println("COMPRADOR: " + comprador);
        System.out.println("----------------------");
        System.out.println("VEHÍCULO VENDIDO:");
        vehiculo.mostrarDetalles();  // Polimorfismo en acción
        System.out.println("----------------------");
        System.out.println("TOTAL: $" + vehiculo.getPrecio());
    }
} 
```


