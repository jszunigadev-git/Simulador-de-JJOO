# Simulador de JJOO
Simulador de JJOO es un proyecto personal desarrollado en Python enfocado en aplicar prácticas avanzadas de Programación Orientada a Objetos (POO) y arquitectura limpia. El sistema permite gestionar eventos deportivos, inscripciones de atletas y simulaciones competitivas a través de una interfaz interactiva por terminal.

## Características Principales
**Modularidad Estricta y Arquitectura Limpia:** Separación absoluta entre la lógica de control del menú (menu.py), las entidades del negocio y las utilidades visuales.

**Gestión Inteligente de Memoria (Registry Pattern):** Implementación de lógica personalizada para prevenir la duplicidad de objetos en memoria. El sistema detecta automáticamente si un atleta ya existe globalmente para reutilizar su instancia y centralizar su historial deportivo.
<details>
<summary><b>Ver estructura del menú principal</b></summary>
  
```python
    @classmethod    
    def obtener_o_crear(cls, nombre: str, pais: str) -> Atleta:
        """Método de clase encargado de verificar que el atleta sea único reutilizando su instancia e historial en memoria."""
        atleta_temp = cls(nombre, pais)
        
        # El operador 'in' y '.index()' buscan por Nombre+País gracias a la sobrecarga de __eq__
        if atleta_temp in cls.listado_atletas:
            indice = cls.listado_atletas.index(atleta_temp)
            return cls.listado_atletas[indice]
        
        cls.listado_atletas.append(atleta_temp)
        return atleta_temp
```
</details>

**Sobrecarga de Operadores (__eq__):** Modificación del comportamiento nativo de comparación en Python para validar la unicidad de participantes basándose en combinaciones de atributos (Nombre + País), permitiendo homónimos de diferentes naciones de forma segura.

**Decoradores Personalizados Reutilizables:** Creación de decoradores estéticos para encapsular y estandarizar el formateo visual de las listas en la terminal, manteniendo el código principal bajo el principio DRY

**Estructuras de Datos Eficientes:** Uso de List Comprehensions y almacenamiento de medallas mediante tuplas contextualizadas (Tipo, Deporte) para optimizar la creación de informes y tabulaciones.

# Tecnologías Utilizadas
**Lenguaje:** Python 3.10+. **Paradigma:** Programación Orientada a Objetos Avanzada (POO).
