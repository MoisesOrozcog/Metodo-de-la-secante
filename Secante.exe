#include <iostream>
#include <cmath>
#include <iomanip>

using namespace std;

class calculadora {
private:
    double inicio;
    double fin;
    int numPuntos;
    int numFix;

public:
//En el siguiente metodo pedimos al usuario el rango que desea calcular y las C.S.
    void ingresarRango() {
        cout << "Ingresa el inicio del rango: ";
        cin >> inicio;

        cout << "Ingresa el fin del rango: ";
        cin >> fin;

        cout << "Ingresa el numero total de evaluaciones que quieres ver: ";
        cin >> numPuntos;

        cout << "Ingresa el numero de cifras significativas: ";
        cin >> numFix;

        cout << endl;
    }

//En el siguiente metodo tenemos la funcion que se va a evaluar, el metodo resive el valor de x y regresa la funcion ya evaluada
    double calcularFuncion(double x) {
        return (x * sin(x)) - 1;
    }

//En el siguiente metodo se imprime la tabla de resultados con el rango y su respectiva respuesta
    void imprimirTabla() {
        cout<< "Sustituyendo los valores del rango ingresado en la variable x en la siguiente funciones, tenemos la siguiente tabla de resultados: "<<endl;
        cout<<"f(x) = (x * sin(x)) - 1"<<endl<<endl;

        cout << "Tabla de resultados:" << endl;
        cout << setw(10) << "x" << setw(15) << "f(x)" << endl;  //setw es para darle estructura a la tabla, el numero indica los espacios que ocupa para no tener todo chueco
        cout << "-----------------------" << endl;

        double paso = (fin - inicio) / (numPuntos - 1);     //aqui se calcula el tamaño del paso entre cada punto del rango, esto nos da la distancia entre cada valor consecutivo de x
        double x = inicio;      //se inicializa la variable x con el valor inicial "inicio"

        cout << fixed;      //utilizamos cout para configurar la salida decimal fija
        cout << setprecision(numFix);       //en esta parte se aplica el fix

        for (int i = 0; i < numPuntos; i++) {       //se inicia el bucle for para calcular la funcion con respecto de x y el numero de puntos
            double resultado = calcularFuncion(x);
            cout << setw(10) << x << setw(15) << resultado << endl;
            x += paso;
        }
    }
};

//Inicializamos la clase Secante para poder calcular
class Secante {
private:
    double x0;   // Valor inicial x0
    double x1;   // Valor inicial x1
    int iteracionesMaximas;   // Número máximo de iteraciones

public:
//En esta parte solo inicializamos las variables a utilizar y las igualamos a las variables ya declaradas en el private
    Secante(double x0, double x1, int iterMax) {
        this->x0 = x0;
        this->x1 = x1;
        this->iteracionesMaximas = iterMax;
    }
//Reciclamos parte del codigo para poder evaluar una vez mas la funcion
    double calcularFuncion(double x) {
        return (x * sin(x)) - 1;  // Función f(x) = (x * sin(x)) - 1
    }
//En esta parte del codigo buscamos imprimir la tabla de resultados, mostrando previamente la formula de Secante
    void imprimirTabla() {

        cout<<endl;

        cout<<"Formula de Secante: "<<endl;
        cout<<"x = x1 - ((fx1 * (x1 - x0)) / (fx1 - fx0))"<<endl;

        cout<<endl;

        cout << "Tabla de resultados:" << endl;
        cout << setw(10) << "Iteracion" << setw(15) << "x" << setw(15) << "f(x)" << setw(15) << "Error Relativo" << endl;
        cout << "------------------------------------------------------" << endl;
//Igualamos las variables respectivamente al uso que tenga dentro de la formula
        int iteracion = 0;
        double xAnterior = x0;
        double xActual = x1;
        double errorRelativo = 1;
//Empezamos a crear el bucle
        do {
//Declaramos las variables de las evaluaciones de f y los igualamos al metodo calcularFuncion mandandole los valores correspondientes para que se evalue en la funcion
            double fAnterior = calcularFuncion(xAnterior);
            double fActual = calcularFuncion(xActual);
//Ingresamos los valores para la formula de Secante y luego hacemos igualaciones para poder hacer la siguiente iteracion o calculo
            double xSiguiente = xActual - ((fActual * (xAnterior - xActual)) / (fAnterior - fActual));
            xAnterior = xActual;
            xActual = xSiguiente;
//Se suma 1 a la iteraccion hasta que sea igual al numero de iteraciones que el usuario ingreso por teclado
            iteracion++;
//Agregamos un if else para detectar si se puede calcular el error relativo, siendo que iteracion sea mayor a 1 para que se calcule el error relativo
            if(iteracion>1){
                errorRelativo = abs((xActual - xAnterior) / xActual);
            }else{
                errorRelativo = 1;
            }
			if (errorRelativo == 0 || &calcularFuncion == 0) {
    		break; }
			
            cout << setw(10) << iteracion << setw(15) << xActual << setw(15) << calcularFuncion(xActual) << setw(15) << errorRelativo << endl;

        } while (iteracion < iteracionesMaximas);

        cout << "------------------------------------------------------" << endl;
        cout << "Resultado: x = " << xActual << endl << endl;
        //cout << "A partir de la iteracion: " << iteracion << "el error relativo es igual a 0."<<endl;
    }
};

int main() {
//Mandamos a llamar los metodos anteriormente explicados 
    calculadora calcu;
    calcu.ingresarRango();
    calcu.imprimirTabla();

//Declaramos variables para la clase Secante y empezamos a pedirle los valores al usuario
    double x0, x1;
    int iteracionesMaximas;

    cout << endl;

    cout << "Ingrese el valor inicial x0: ";
    cin >> x0;

    cout << "Ingrese el valor inicial x1: ";
    cin >> x1;

    cout << "Ingrese el numero maximo de iteraciones: ";
    cin >> iteracionesMaximas;

//Mandamos los valores ingresados por el usuaio a la clase Secante para que haga el proceso y terminamos llamando al metodo tabla para mostrar respuestas
    Secante secante(x0, x1, iteracionesMaximas);
    //secante.imprimirEvaluaciones();
    secante.imprimirTabla();

    return 0;
}
