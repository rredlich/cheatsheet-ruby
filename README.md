# CheatSheet de Ruby

## Lo básico

```ruby
# Esto es un comentario de una línea

=begin
Y esto un comentario
de más de una línea
=end

puts "Esto se imprimirá en el terminal"
# > Esto se imprimirá en el terminal

# Variables numéricas
x = 1   # Entero
y = 2.3 # Flotante

puts 2+5    # Suma e imprime 7
puts 4-2    # Resta e imprime 2
puts 10/2   # Divide e imprime 5
puts 5*2    # Multiplica e imprime 10
puts 2**4   # 2 con exponente 4 e imprime 16
puts 7%3    # 7 módulo 3 e imprime 1

# Variables booleanas
verdadero = true
falso = false
falso2 = !verdadero

# Otros operadores de asignación
x = 1
x += 1   # x = 1 + 1 = 2
x -= 1   # x = 2 - 1 = 1
x *= 2   # x = 1 * 2 = 2
x /= 2   # x = 2 / 2 = 1
```

### Strings
```ruby
s1 = 'Soy un String'
s2 = "También soy un String"

puts s1.length   # Obtiene el largo e imprime 13
puts s1.length   # Invierte el string e imprime gnirtS nu yoS
puts s1.upcase   # Convierte a mayúsculas e imprime SOY UN STRING
puts s1.downcase # Convierte a minúsculas e imprime soy un string

edad = 10
puts "Hola, tengo #{edad} años"
# > Hola, tengo 10 años

# Se pueden concatenar strings
puts "Soy el 1er string, " + "y yo el 2do"
# > Soy el 1er string, y yo el 2do

edad = "10"       # edad es un String "10"
edad = edad.to_i  # edad se convierte a entero 10
```

## Control de flujo
```ruby
# Solo una condición
if edad == 10
  puts "Tienes 10 años!"
end

# La versión de una línea
puts "Tienes 10 años" if edad == 10

# Condición If y Else
if edad > 50 
  puts "Tienes más de 50 años"
else
  puts "Tienes 50 años o menos" 
end

# Condición compleja con Else If
if edad == 5
  puts "Tienes 5 años"
elsif edad == 10
  puts "Tienes 10 años"
elsif edad == 15
  puts "Tienes 15 años"
else
  puts "No tienes 5, 10 ni 15 años"
end

# Condiciones con case
momento = "mañana"

case momento
  when "mañana"
    puts "Buenos días"
  when "tarde"
    puts "Buenas tardes"
  else
    puts "Hola"
end
# > Buenos días

# Operador ternario
edad = 12
puts edad >= 18 ? "Eres mayor de edad" : "Eres menor de edad"
# > Eres menor de edad
```

### Operadores lógicos
| Operador | Descripción |
| -------- | ----------- |
| == | Igual qué |
| != | Distinto qué |
| < | Menor qué |
| <= | Menor o igual qué |
| > | Mayor qué |
| >= | Mayor o igual qué |
| \|\| | Or lógico |
| && | And lógico | 

```ruby
# Comparando dos cosas
a == b

# Comparando varias condiciones
a == b || c >= d

# Dentro de una condición
if edad > 10 && edad < 20 do
  puts "Tienes más de 10 y menos de 20 años"
end
```

## Loops
```ruby
# Loop for de 1 a 5
for i in 1..5
  puts i
end
# > 1
# > 2
# > 3
# > 4
# > 5

# Loop for de 1 a 5 saltando los números pares
# next se usa para saltar a la siguiente iteración
for i in 1..5
  next if i % 2 == 0
  puts i
end
# > 1
# > 3
# > 5

# Ejecuta un bloque utilizando el método times
5.times { puts "Hola" }
# > Hola
# > Hola
# > Hola
# > Hola
# > Hola
```
## Arreglos, Hashes y Símbolos
### Arreglos
```ruby
num = [1, 2, 3, 4, 5]
 
palabras = ["hola", "soy", "un", "array"]
 
mezclados = ["hola", true, 2, 1.5]

vacio = []

num << 6
puts num
# [1, 2, 3, 4, 5, 6]

# Los arreglos se pueden indexar
# El primer elemento siempre es el 0
puts mezclados[2] # > true
puts mezclados[0] # > hello

# Para arreglos de múltiples dimensiones
arreglo_2D = [[1,2,3,4,5],["hola", true, 2, 1.5]]
 
# El arreglo con índice 1 es el segundo
puts arreglo_2D[1] # > ["hola", true, 2, 1.5]
 
# También se puede acceder a un elemento particular
puts arreglo_2D[0][2] # > 3

# El método each se usa para recorrer los arreglos
palabras = ["hola", "soy", "un", "array"]
palabras.each { |palabra| puts palabra }
# > hola
# > soy
# > un
# > array
```

### Hashes
```ruby
# Un hash es una colección de pares key-valor
perfil = {
  "nombre" => "Jon",
  "apellido" => "Snow"
  "telefono" => 1234567
}
 
puts perfil["nombre"] # > Jon

# Para agregar un nuevo par key-valor
perfil["edad"] = 35

# Para inicializar un Hash
vacio = Hash.new
puts vacio # > {}

# El método each también se usa para recorrer hashes
perfil = {
  "nombre" => "Jon",
  "apellido" => "Snow"
  "telefono" => 1234567
}

perfil.each do |key, valor|
  puts "Mi #{key} es #{valor}."
end
# > Mi nombre es Jon.
# > Mi apellido es Snow.
# > Mi telefono es 1234567.
```
### Hashes y símbolos
```ruby
# Los símbolos son nombres inmutables usados principalmente como hash keys. Se pueden definir en hashes de dos formas, usando => o :
perfil = {
  :nombre => "Jon",
  :apellido => "Snow",
  :telefono => 1234567
}

perfil = {
  nombre: "Jon",
  apellido: "Snow",
  telefono: 1234567
}

# En ambos casos se llama al valor de la siguiente forma
puts perfil[:nombre]
# > Jon

# Se puede utilizar el método select para obtener valores que cumplan un criterio
tiempos = {
  Jon: 15.5,
  Arya: 16.8,
  Bran: 21.0
}
 
tiempos.select { |nombre, tiempo| tiempo <  20.0 }
# Retorna {:Jon=>15.5, :Arya=>16.8}

# Tambien podemos iterar por los keys o valores con el método each_key y each_value
tiempos.each_key { |k| puts k }
# > Jon
# > Arya
# > Bran
 
tiempos.each_value { |v| puts v }
# > 15.5
# > 16.8
# > 21.0
```

## Métodos
```ruby
# Un método sin argumento
def saluda
  puts "¡Hola Mundo!"
end

# Para llamar al método
saluda()
# > ¡Hola Mundo!

# Un método con argumentos
def exponente(num, exp)
  return num ** exp
end

puts exponente(2,4)
# > 16

# Se puede usar el operador * antes de un argumento para indicar que puede tener un número desconocido de argumentos
def lista_de_nombres(*nombres)
  nombres.each { |nombre| puts "Yo soy #{nombre}" }
end
 
lista_de_nombres("Jon", "Arya", "Bran") 
# > Yo soy Jon
# > Yo soy Arya
# > Yo soy Bran
```