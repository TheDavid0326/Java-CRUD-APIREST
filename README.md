# Aplicación Spring Boot para API REST de Productos

Este código implementa una aplicación Spring Boot que expone una API RESTful para gestionar productos.

## Entidad Producto (Product.java)

La clase `Product` representa la entidad Producto del dominio del problema. Se mapea a una tabla en la base de datos.

* **`@Entity`:** Indica que esta clase es una entidad JPA.
* **`@Id`:** Marca la propiedad `id` como la clave primaria de la entidad.
* **`@GeneratedValue(strategy = GenerationType.IDENTITY)`:** Indica que el valor del `id` se genera automáticamente por la base de datos utilizando una estrategia de autoincremento.
* **`private long id;`:** Identificador único del producto.
* **`private String name;`:** Nombre del producto.
* **`private double price;`:** Precio del producto.

## Controlador de Productos (ProductController.java)

La clase `ProductController` es un controlador REST que maneja las solicitudes HTTP relacionadas con los productos.

* **`@RestController`:** Indica que esta clase es un controlador REST de Spring.
* **`@RequestMapping("/products")`:** Define la ruta base para todas las solicitudes manejadas por este controlador. En este caso, todas las solicitudes relacionadas con productos estarán prefijadas con "/products".
* **`@Autowired private IProductRepository productRepository;`:** Inyección de dependencia del repositorio de productos.

### Métodos del Controlador

* **`@GetMapping`:** Asigna este método para manejar solicitudes GET a la ruta "/products".
    * `public List<Product> getAllProducts()`: Recupera todos los productos de la base de datos utilizando el repositorio y los devuelve en una lista.
* **`@GetMapping("/{id}")`:** Asigna este método para manejar solicitudes GET a la ruta "/products/{id}".
    * `public Product getProductById(@PathVariable Long id)`: Recupera un producto por su identificador. Si no se encuentra el producto, se lanza una excepción.
* **`@PostMapping`:** Asigna este método para manejar solicitudes POST a la ruta "/products".
    * `public Product createProduct(@RequestBody Product product)`: Crea un nuevo producto utilizando la información del cuerpo de la solicitud y lo guarda en la base de datos utilizando el repositorio.
* **`@PutMapping("/{id}")`:** Asigna este método para manejar solicitudes PUT a la ruta "/products/{id}".
    * `public Product updateProduct(@PathVariable Long id, @RequestBody Product product)`: Actualiza un producto existente. Primero se recupera el producto por su identificador, luego se actualizan sus propiedades con los valores del cuerpo de la solicitud y finalmente se guarda en la base de datos utilizando el repositorio.
* **`@DeleteMapping("/{id}")`:** Asigna este método para manejar solicitudes DELETE a la ruta "/products/{id}".
    * `public String deleteProduct(@PathVariable Long id)`: Elimina un producto por su identificador. Si no se encuentra el producto, se lanza una excepción.

## Aplicación Principal (ApirestApplication.java)

La clase `ApirestApplication` es el punto de entrada de la aplicación Spring Boot.

* **`@SpringBootApplication`:** Anotación que habilita funcionalidades de Spring Boot de forma automática.
* **`public static void main(String[] args) { SpringApplication.run(ApirestApplication.class, args); }`:** Método principal que inicia la aplicación Spring Boot.

## Ejecutar la aplicación

1. Asegúrate de tener Maven instalado.
2. Abre un terminal en la ubicación del proyecto.
3. Ejecuta el comando `mvn clean install` para compilar el proyecto.
4. Ejecuta el comando `mvn spring-boot:run` para iniciar la aplicación.

## Resumen

Este código implementa una API REST básica para gestionar productos utilizando Spring Boot y JPA. El controlador proporciona métodos para consultar, crear, actualizar y eliminar productos. La aplicación se inicia mediante la clase `ApirestApplication`.

## Consideraciones adicionales

* **Dependencias:** Este código asume que las dependencias necesarias para Spring Boot y JPA están configuradas en el pom.xml del proyecto.
* **Base de datos:** La aplicación necesita una base de datos configurada para persistir los datos de los productos.

Este documento proporciona una descripción general de la aplicación Spring Boot para la API REST de productos. Puedes consultarlo como referencia para comprender la estructura del proyecto y cómo funciona la interacción entre las clases para gestionar productos a través de una API REST.
