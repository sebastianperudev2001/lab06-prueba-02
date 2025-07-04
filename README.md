

# Laboratorio 20/06

> Sebastián Chávarry

## Ejercicio 01 - Pruebas unitarias (caja blanca)

### Instrucciones
1. Analizar la clase `ShoppingCart`.
2. Desarrollar dos pruebas unitarias con JUnit:
   - Un caso de prueba **válido (happy path)**.
   - Un caso de prueba **inválido (unhappy path)** que dispare una excepción.

### Clase a testear
```
import java.util.ArrayList;
import java.util.List;

public class ShoppingCart {
    private List<Double> productPrices;

    public ShoppingCart() {
        this.productPrices = new ArrayList<>();
    }

    public void addProduct(double price) {
        if (price <= 0) throw new IllegalArgumentException("Price must be positive");
        productPrices.add(price);
    }

    public void removeProduct(double price) {
        productPrices.remove(price); 
    }

    public double getTotal() {
        double total = 0;
        for (double price : productPrices) {
            total += price;
        }
        return total;
    }

    public int getProductCount() {
        return productPrices.size();
    }
}
```
---

## Ejercicio 02 - Caja blanca: grafo de flujo de control

### Instrucciones

1. Analizar la clase `TransactionAnalyzerV2`.
2. Dibujar el grafo de flujo de control correspondiente.
3. Identificar y listar los caminos linealmente independientes.
4. Proponer al menos un caso de prueba por cada camino independiente.

### Clase base

```java
public class TransactionAnalyzerV2 {
    public String analyzeTransactions(double[] transactions, double balance, boolean accountFrozen) {
        String status = "Spending OK";
        double totalSpent = 0;

        if (accountFrozen) {
            status = "Account Frozen";
        } else {
            for (double t : transactions) {
                if (t < 0) {
                    totalSpent += -t;
                }
            }
        }

        return status;
    }
}
```

### Entregables esperados

* Grafo de flujo de control en imagen (hecho a mano o digital).
* Lista de caminos independientes.
* Tabla con casos de prueba correspondientes a cada camino.

---

## Ejercicio 03 - Caja negra: partición equivalente

### Instrucciones

1. Analizar nuevamente la clase `LoanEligibilityChecker`.
2. Identificar clases de equivalencia válidas e inválidas para cada parámetro de entrada.
3. Proponer al menos cuatro casos de prueba representativos.
4. Presentar los casos en tabla con justificación.

### Clase base

```java
public class LoanEligibilityChecker {
    public String checkEligibility(int age, double income, int creditScore) {
        if (age < 18) {
            return "Rejected: Underage";
        }
        if (income < 1500) {
            return "Rejected: Insufficient Income";
        }
        if (creditScore < 600) {
            return "Rejected: Low Credit Score";
        }
        return "Approved";
    }
}
```
---
## Entregables

* Código de pruebas unitarias en JUnit para el Ejercicio 01.
* Imagen del grafo de flujo de control, lista de caminos y casos de prueba para el Ejercicio 02.
* Tabla de partición equivalente para el Ejercicio 03.

---

## Fecha de entrega

**Sábado 21 de junio de 2025 - 12:00**
