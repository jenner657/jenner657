-#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

// Funciones para las operaciones de la biblioteca

void retirarLibro(vector<string>& libros, const string& libro) {
    auto it = find(libros.begin(), libros.end(), libro);

    if (it != libros.end()) {
        libros.erase(it);
        cout << "Libro'" << libro << "' retirado con éxito." << endl;
    } else {
        cout << "Libro '" << libro << "' no encontrado." << endl;
    }
}

void devolverLibro(vector<string>& libros, const string& libro) {
    libros.push_back(libro);
    cout << "Libro '" << libro << "' devuelto con éxito." << endl;
}

void verificarExistencia(const vector<string>& libros, const string& libro) {
    auto it = find(libros.begin(), libros.end(), libro);

    if (it != libros.end()) {
        cout << "El libro '" << libro << "' existe en la biblioteca." << endl;
    } else {
        cout << "El libro '" << libro << "' no existe en la biblioteca." << endl;
    }
}

void mostrarLibros(const vector<string>& libros) {
    vector<string> librosOrdenados = libros;
    sort(librosOrdenados.begin(), librosOrdenados.end());

    cout << "1984, de George Orwell" << endl;
    cout << "Crimen y castigo, de Fiódor Dostoyevski.  " << endl;
    cout << "El señor de los anillos (Trilogía), de J. R. R. Tolkien.  389 puntos" << endl;
    cout << "Lolita, de Vladimir Nabokov" << endl;
    cout << "Madame Bovary, de Gustave Flaubert.  " << endl;
     cout << "Orgullo y prejuicio, de Jane Austen.  " << endl;
     cout << "Ulises, de James Joyce.  " << endl;
     cout << "Un mundo feliz, de Aldous Huxley" << endl;
    for (const string& libro : librosOrdenados) {
        cout << libro << endl;
    }
}

int main() {
    vector<string> libros;

    while (true) {
        // Menú principal
        cout << "----- Menú Principal -----" << endl;
        cout << "1. Retirar libro" << endl;
        cout << "2. Devolver libro" << endl;
        cout << "3. Verificar existencia de un libro" << endl;
        cout << "4. Mostrar libros existentes" << endl;
        cout << "5. Salir" << endl;
        cout << "--------------------------" << endl;

        int opcion;
        cout << "Seleccione una opción (1-5): ";
        cin >> opcion;

        switch (opcion) {
            case 1: {
                string libroRetirar;
                cout << "Ingrese el nombre del libro a retirar: ";
                cin.ignore();
                getline(cin, libroRetirar);
                retirarLibro(libros, libroRetirar);
                break;
            }
            case 2: {
                string libroDevolver;
                cout << "Ingrese el nombre del libro a devolver: ";
                cin.ignore();
                getline(cin, libroDevolver);
                devolverLibro(libros, libroDevolver);
                break;
            }
            case 3: {
                string libroVerificar;
                cout << "Ingrese el nombre del libro a verificar: ";
                cin.ignore();
                getline(cin, libroVerificar);
                verificarExistencia(libros, libroVerificar);
                break;
            }
            case 4:
                mostrarLibros(libros);
                break;
            case 5:
                cout << "¡Hasta luego!" << endl;
                return 0;
            default:
                cout << "Opción no válida. Por favor, ingrese un número del 1 al 5." << endl;
                break;
        }
    }

    return 0;
}
