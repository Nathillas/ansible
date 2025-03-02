# ANSIBLE

## **1\. Nombre y descripción del módulo**

**Nombre:** ansible.builtin.debug

**Descripción**: Este módulo se utiliza para imprimir declaraciones durante la ejecución de un playbook. Es extremadamente útil para depuración, para mostrar el valor de variables, o para proporcionar información sobre el progreso de la ejecución del playbook\[1\].

## **2\. Ejemplos de funcionamiento**

### **Ejemplo 1: Mostrar un mensaje simple**

```
- name: Imprimir mensaje de depuración  
  ansible.builtin.debug:  
    msg: "Este es un mensaje de depuración"
 ```  

Este ejemplo imprime un mensaje durante la ejecución del playbook.

![][image1]

### **Ejemplo 2: Mostrar el valor de una variable**

```
- name: Mostrar el nombre del host
  ansible.builtin.debug:
    var: ansible\_hostname
```

Este ejemplo muestra el valor de la variable `ansible_hostname`.

![][image2]

### **Ejemplo 3: Usar expresiones condicionales**

```
- name: Verificar espacio en disco

  ansible.builtin.command: df \-h /

  register: df\_result

- name: Mostrar advertencia si el espacio es bajo

  ansible.builtin.debug:

    msg: "Advertencia: Espacio en disco bajo"

  when: df\_result.stdout.find('80%') \!= \-1
```

Este ejemplo muestra un mensaje de advertencia si el espacio en disco está por encima del 80%.

![][image3]

## **3\. Características clave**

1. Simplicidad: Es muy fácil de usar y entender.  
2. Flexibilidad: Puede mostrar texto estático, variables, o resultados de expresiones.  
3. Útil para depuración: Ayuda a entender el estado de las variables y el flujo de ejecución.  
4. No realiza cambios: Es seguro de usar ya que solo muestra información, no modifica nada.

## **4\. Usos comunes**

* Depurar playbooks mostrando valores de variables en diferentes etapas.  
* Proporcionar retroalimentación visual durante la ejecución de tareas largas.  
* Verificar el resultado de operaciones condicionales.  
* Mostrar resúmenes o estadísticas al final de un playbook.

## **5\. Parámetros importantes**

* `msg`: El mensaje a mostrar.  
* `var`: El nombre de la variable cuyo valor se quiere mostrar.  
* `verbosity`: Nivel de detalle (0 por defecto, valores más altos requieren más `-v` en la línea de comando).

## **6\. Referencias**

\[1\] [https://docs.ansible.com/ansible/latest/collections/ansible/builtin/debug\_module.html](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/debug_module.html)

\[2\] [https://www.middlewareinventory.com/blog/ansible-debug-module/](https://www.middlewareinventory.com/blog/ansible-debug-module/)

\[3\] [https://www.redhat.com/sysadmin/ansible-debug-troubleshoot](https://www.redhat.com/sysadmin/ansible-debug-troubleshoot)

El módulo `ansible.builtin.debug` es una herramienta esencial en el arsenal de cualquier usuario de Ansible. Su simplicidad lo hace ideal para principiantes, pero su utilidad lo mantiene como una herramienta frecuentemente utilizada incluso por usuarios avanzados. Es particularmente valioso durante el desarrollo y la depuración de playbooks complejos.

