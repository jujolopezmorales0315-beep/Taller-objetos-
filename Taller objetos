#include <iostream>
#include <string>
#include <vector>
using namespace std;

/* ============================================================
   NIVEL 1 - GETTERS, SETTERS y CLASES SIMPLES
   ============================================================ */

/* ----------------- Ejercicio 1.1 - Vehículo ---------------- */
class Vehiculo {
private:
    string marca, modelo;
    int año;
    double velocidadMaxima;

public:
    Vehiculo(string m, string mod, int a, double v) {
        marca = m;
        modelo = mod;
        setAño(a);
        setVelocidadMaxima(v);
    }

    // Getters
    string getMarca() const { return marca; }
    string getModelo() const { return modelo; }
    int getAño() const { return año; }
    double getVelocidadMaxima() const { return velocidadMaxima; }

    // Setters
    void setMarca(string m) { marca = m; }
    void setModelo(string m) { modelo = m; }

    void setAño(int a) {
        if (a > 1886) año = a;
        else año = 1886;
    }

    void setVelocidadMaxima(double v) {
        if (v > 0) velocidadMaxima = v;
        else velocidadMaxima = 0;
    }

    void acelerar(double incremento) {
        if (incremento > 0) velocidadMaxima += incremento;
    }

    virtual void mostrarInfo() const {
        cout << "Vehículo: " << marca << " " << modelo
             << " | Año: " << año
             << " | Velocidad Max: " << velocidadMaxima << " km/h\n";
    }
};

/* ---------------- Ejercicio 1.2 - Producto ------------------ */
class Producto {
private:
    string codigo, nombre;
    double precio;
    int cantidad;

public:
    Producto(string c, string n, double p, int cant) {
        codigo = c;
        nombre = n;
        setPrecio(p);
        setCantidad(cant);
    }

    string getCodigo() const { return codigo; }
    string getNombre() const { return nombre; }
    double getPrecio() const { return precio; }
    int getCantidad() const { return cantidad; }

    void setPrecio(double p) {
        precio = (p >= 0) ? p : 0;
    }

    void setCantidad(int c) {
        cantidad = (c >= 0) ? c : 0;
    }

    double calcularValorTotal() const {
        return precio * cantidad;
    }

    void aplicarDescuento(double porcentaje) {
        if (porcentaje > 0 && porcentaje <= 100)
            precio -= precio * (porcentaje / 100);
    }

    void mostrarInfo() const {
        cout << "Producto: " << nombre << " (Cod: " << codigo << ")"
             << " | Precio: $" << precio
             << " | Cantidad: " << cantidad << "\n";
    }
};

/* ============================================================
   NIVEL 2 - HERENCIA SIMPLE
   ============================================================ */

/* ------------------ Clase Auto ------------------------------ */
class Auto : public Vehiculo {
private:
    int numeroPuertas;
    string tipoCombustible;

public:
    Auto(string m, string mod, int a, double v, int puertas, string combustible)
        : Vehiculo(m, mod, a, v) {
        numeroPuertas = puertas;
        tipoCombustible = combustible;
    }

    void mostrarInfo() const override {
        Vehiculo::mostrarInfo();
        cout << "  Puertas: " << numeroPuertas
             << " | Combustible: " << tipoCombustible << "\n";
    }
};

/* ------------------ Clase Motocicleta ----------------------- */
class Motocicleta : public Vehiculo {
private:
    bool tieneAlaron;
    int cilindrada;

public:
    Motocicleta(string m, string mod, int a, double v, bool alaron, int cil)
        : Vehiculo(m, mod, a, v) {
        tieneAlaron = alaron;
        cilindrada = cil;
    }

    void mostrarInfo() const override {
        Vehiculo::mostrarInfo();
        cout << "  Alarón: " << (tieneAlaron ? "Sí" : "No")
             << " | Cilindrada: " << cilindrada << "cc\n";
    }
};

/* ------------------ Empleado Base --------------------------- */
class Empleado {
protected:
    string nombreCompleto, numeroEmpleado;
    double salarioBase;

public:
    Empleado(string n, string num, double s)
        : nombreCompleto(n), numeroEmpleado(num), salarioBase(s) {}

    virtual double calcularSalarioTotal() const = 0;

    virtual void mostrarInfo() const {
        cout << nombreCompleto << " | Num: " << numeroEmpleado
             << " | Salario Base: $" << salarioBase << "\n";
    }

    virtual ~Empleado() {}
};

class EmpleadoTiempoCompleto : public Empleado {
private:
    string beneficios;
    double bono;

public:
    EmpleadoTiempoCompleto(string n, string num, double s, string b, double bo)
        : Empleado(n, num, s), beneficios(b), bono(bo) {}

    double calcularSalarioTotal() const override {
        return salarioBase + bono;
    }

    void mostrarInfo() const override {
        Empleado::mostrarInfo();
        cout << "  Beneficios: " << beneficios
             << " | Bono: $" << bono << "\n";
    }
};

class EmpleadoPorHoras : public Empleado {
private:
    int horasTrabajadas;
    double tarifaHora;

public:
    EmpleadoPorHoras(string n, string num, double s, int h, double t)
        : Empleado(n, num, s), horasTrabajadas(h), tarifaHora(t) {}

    double calcularSalarioTotal() const override {
        return horasTrabajadas * tarifaHora;
    }

    void mostrarInfo() const override {
        Empleado::mostrarInfo();
        cout << "  Horas: " << horasTrabajadas
             << " | Tarifa: $" << tarifaHora << "\n";
    }
};

/* ============================================================
   NIVEL 3 - HERENCIA MULTINIVEL
   ============================================================ */

/* ------------------ Clase Animal ---------------------------- */
class Animal {
protected:
    string nombre;
    int edad;
    double peso;

public:
    Animal(string n, int e, double p) : nombre(n), edad(e), peso(p) {}
    virtual void hacerSonido() const = 0;

    virtual void mostrarInfo() const {
        cout << nombre << " | Edad: " << edad << " | Peso: " << peso << "kg\n";
    }

    virtual ~Animal() {}
};

/* ------------------ Mamífero ------------------------------- */
class Mamifero : public Animal {
protected:
    bool tieneCola;

public:
    Mamifero(string n, int e, double p, bool cola)
        : Animal(n, e, p), tieneCola(cola) {}

    void mostrarInfo() const override {
        Animal::mostrarInfo();
        cout << "  Tiene cola: " << (tieneCola ? "Sí" : "No") << "\n";
    }
};

/* ------------------ Ave ------------------------------------ */
class Ave : public Animal {
protected:
    double envergaduraAlas;

public:
    Ave(string n, int e, double p, double ala)
        : Animal(n, e, p), envergaduraAlas(ala) {}

    void mostrarInfo() const override {
        Animal::mostrarInfo();
        cout << "  Envergadura: " << envergaduraAlas << "m\n";
    }
};

/* ------------------ Animales Finales ----------------------- */
class Perro : public Mamifero {
public:
    Perro(string n, int e, double p, bool cola) : Mamifero(n, e, p, cola) {}
    void hacerSonido() const override { cout << "Guau!\n"; }
};

class Gato : public Mamifero {
public:
    Gato(string n, int e, double p, bool cola) : Mamifero(n, e, p, cola) {}
    void hacerSonido() const override { cout << "Miau!\n"; }
};

class Loro : public Ave {
public:
    Loro(string n, int e, double p, double ala) : Ave(n, e, p, ala) {}
    void hacerSonido() const override { cout << "Prrrr!\n"; }
};

class Aguila : public Ave {
public:
    Aguila(string n, int e, double p, double ala) : Ave(n, e, p, ala) {}
    void hacerSonido() const override { cout << "Screeeee!\n"; }
};

/* ============================================================
   NIVEL 4 - SISTEMA UNIVERSITARIO
   ============================================================ */

class Persona {
protected:
    string nombre;
    int edad;
    string cedula;

public:
    Persona(string n, int e, string c) : nombre(n), edad(e), cedula(c) {}

    virtual void mostrarInfo() const {
        cout << nombre << " | Edad: " << edad << " | CC: " << cedula << "\n";
    }
};

/* ---------------- Clase Curso ------------------------------ */
class Curso {
private:
    string codigo, nombre;
    int creditos;
    string profesor;

public:
    Curso(string c, string n, int cr, string p)
        : codigo(c), nombre(n), creditos(cr), profesor(p) {}

    void mostrarInfo() const {
        cout << nombre << " (" << codigo << ") - " << creditos
             << " créditos | Prof: " << profesor << "\n";
    }
};

/* ---------------- Estudiante ------------------------------- */
class Estudiante : public Persona {
private:
    string carrera;
    double promedio;
    int semestre;
    vector<Curso> cursos;

public:
    Estudiante(string n, int e, string c, string car, double pr, int s)
        : Persona(n, e, c), carrera(car), promedio(pr), semestre(s) {}

    void matricularCurso(const Curso& curso) {
        cursos.push_back(curso);
    }

    double calcularPromedioActual() const {
        return promedio;
    }

    void mostrarInfo() const override {
        Persona::mostrarInfo();
        cout << "  Carrera: " << carrera
             << " | Promedio: " << promedio
             << " | Semestre: " << semestre << "\n";
    }
};

/* ---------------- Profesor --------------------------------- */
class Profesor : public Persona {
private:
    string especialidad;
    int aniosExp, numEstudiantes;

public:
    Profesor(string n, int e, string c, string esp, int a, int ne)
        : Persona(n, e, c), especialidad(esp), aniosExp(a), numEstudiantes(ne) {}

    bool estaDisponible(int hora) const {
        return hora >= 8 && hora <= 16;
    }

    void mostrarInfo() const override {
        Persona::mostrarInfo();
        cout << "  Especialidad: " << especialidad
             << " | Experiencia: " << aniosExp
             << " años | Estudiantes: " << numEstudiantes << "\n";
    }
};

/* ---------------- Personal --------------------------------- */
class Personal : public Persona {
private:
    string puesto, departamento;
    double salario;

public:
    Personal(string n, int e, string c, string p, string d, double s)
        : Persona(n, e, c), puesto(p), departamento(d), salario(s) {}

    double calcularSalarioMensual() const {
        return salario;
    }

    void mostrarInfo() const override {
        Persona::mostrarInfo();
        cout << "  Puesto: " << puesto
             << " | Dep: " << departamento
             << " | Salario: $" << salario << "\n";
    }
};

/* ============================================================
   MAIN - Ejemplos básicos de uso
   ============================================================ */

int main() {
    cout << "\n=== Vehículo ===\n";
    Vehiculo auto1("Toyota", "Corolla", 2020, 180);
    auto1.mostrarInfo();
    auto1.acelerar(20);
    auto1.mostrarInfo();

    cout << "\n=== Producto ===\n";
    Producto laptop("001", "Laptop HP", 850, 5);
    laptop.mostrarInfo();
    cout << "Valor total: $" << laptop.calcularValorTotal() << "\n";

    cout << "\n=== Auto & Moto ===\n";
    Auto miAuto("Ford", "Mustang", 2023, 220, 4, "Gasolina");
    miAuto.mostrarInfo();

    Motocicleta miMoto("Honda", "CBR600", 2022, 250, true, 600);
    miMoto.mostrarInfo();

    cout << "\n=== Empleados ===\n";
    EmpleadoTiempoCompleto e1("Juan López", "001", 2000, "Seguro médico", 500);
    e1.mostrarInfo();
    cout << "Salario total: $" << e1.calcularSalarioTotal() << "\n";

    EmpleadoPorHoras e2("María García", "002", 0, 40, 15);
    e2.mostrarInfo();
    cout << "Salario total: $" << e2.calcularSalarioTotal() << "\n";

    cout << "\n=== Animales ===\n";
    Perro p("Rex", 5, 25, true);
    p.mostrarInfo();
    p.hacerSonido();

    Aguila a("Águila Real", 3, 5, 1.8);
    a.mostrarInfo();
    a.hacerSonido();

    cout << "\n=== Universidad ===\n";
    Estudiante est("Pedro", 20, "123", "Ingeniería", 4.2, 5);
    est.mostrarInfo();
    est.matricularCurso(Curso("MAT101", "Cálculo", 4, "Dr. Ruiz"));

    Profesor prof("Carla", 40, "987", "Matemáticas", 15, 80);
    prof.mostrarInfo();

    return 0;
}
