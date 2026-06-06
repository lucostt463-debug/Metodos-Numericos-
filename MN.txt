import math
import matplotlib.pyplot as plt
import numpy as np

def calcular_trayectoria_completa(v0, theta_grados, g=9.81):
    """
    Calcula los puntos (x, y) de la trayectoria para graficar.
    """
    theta_rad = math.radians(theta_grados)
    v0x = v0 * math.cos(theta_rad)
    v0y = v0 * math.sin(theta_rad)
    
    # Tiempo total de vuelo
    tv = (2 * v0y) / g
    
    # Generar array de tiempos desde 0 hasta tv
    t = np.linspace(0, tv, num=100)
    
    # Ecuaciones paramétricas del movimiento
    x = v0x * t
    y = (v0y * t) - (0.5 * g * t**2)
    
    return x, y, tv

def graficar_trayectoria(x, y):
    """Genera y muestra el gráfico de la trayectoria."""
    plt.figure(figsize=(10, 5))
    plt.plot(x, y, label='Trayectoria Ideal', color='blue', linewidth=2)
    
    # Estética del gráfico
    plt.title('Simulación de Trayectoria de Proyectil')
    plt.xlabel('Distancia Horizontal (m)')
    plt.ylabel('Altura (m)')
    plt.axhline(0, color='black', linewidth=1) # Eje X
    plt.grid(True, linestyle='--', alpha=0.7)
    plt.legend()
    
    print("\n>> Generando gráfico...")
    plt.show()

def main():
    # ... (Se mantiene la lógica de entrada y validación del código anterior) ...
    v0 = float(input("Ingrese la velocidad inicial (m/s): "))
    theta = float(input("Ingrese el ángulo de lanzamiento (0-90°): "))
    
    # Cálculos para la gráfica
    x_vals, y_vals, tv = calcular_trayectoria_completa(v0, theta)
    
    # Mostrar resultados numéricos (abreviado para este ejemplo)
    print(f"\nAlcance máximo: {x_vals[-1]:.2f} m")
    print(f"Altura máxima: {max(y_vals):.2f} m")
    
    # Visualización
    graficar_trayectoria(x_vals, y_vals)

if __name__ == "__main__":
    main()
