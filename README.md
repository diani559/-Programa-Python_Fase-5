# -Programa-Python_Fase-5
# MATRIZ DEL MENU
# Cada producto tiene: Nombre del producto, Categoria y Precio Base.
menu = [
    ["Hamburguesa", "Comida Rapida", 18000],
    ["Pizza", "Comida Rapida", 25000],
    ["Ensalada", "Saludable", 12000],
    ["Sopa", "Entrada", 10000],
    ["Filete de Res", "Plato Fuerte", 35000],
    ["Jugo Natural", "Bebida", 8000]
]

# FUNCION PARA CALCULAR EL PRECIO FINAL
# Lógica de negocio:
# - Si el producto pertenece a la categoria objetivo
# - Y su precio base es mayor al umbral definido
# Entonces se aplica un 15% de descuento.
# Si no cumple las condiciones, mantiene el precio base.
def calcular_precio_final(producto, categoria_objetivo, umbral):
    nombre, categoria, precio_base = producto
    
    # Nota: Aunque el Filete de Res cuesta 35000 (mayor al umbral),
    # no recibe descuento porque su categoria es "Plato Fuerte"
    # y la promocion solo aplica a la categoria "Comida Rapida".
    
    if categoria == categoria_objetivo and precio_base > umbral:
        precio_final = precio_base * 0.85  # Aplica 15% de descuento
    else:
        precio_final = precio_base         # Mantiene precio base
    
    return precio_final

# PARAMETROS DE LA PROMOCION
categoria_objetivo = "Comida Rapida"
umbral = 20000  # Umbral definido: solo productos con precio mayor a 20000 reciben descuento

# SALIDA DEL PROGRAMA
print("=== Menu con Promocion ===")
for producto in menu:
    precio_final = calcular_precio_final(producto, categoria_objetivo, umbral)
    
    if producto[1] == categoria_objetivo and producto[2] > umbral:
        condicion = "Cumple condiciones, se aplica descuento"
    else:
        condicion = "No cumple condiciones, mantiene precio base"
    
    print(f"{producto[0]} ({producto[1]}) - Precio Base: ${producto[2]} - Precio Final: ${precio_final:.0f} --> {condicion}")
