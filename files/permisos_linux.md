
# Comandos de Linux

## chmod (cambiar los permisos de los archivos)

El comando `chmod` se utiliza para cambiar los permisos de un archivo o directorio. Los permisos determinan quién puede leer, escribir o ejecutar el archivo.

*   **Ejemplo 1**: `chmod 755 archivo`  
    Establece permisos de lectura, escritura y ejecución para el propietario (7), y permisos de lectura y ejecución para los demás (5).

```
ls -l archivo
-rwxr-xr-x 1 usuario grupo 0 date archivo
```

*   **Ejemplo 2**: `chmod +x script.sh`  
    Agrega el permiso de ejecución para el propietario del archivo.

```
ls -l script.sh
-rwxr--r-- 1 usuario grupo 0 date script.sh
```

## chown (cambiar el propietario y grupo de un archivo)

El comando `chown` cambia el propietario y el grupo de un archivo o directorio.

*   **Ejemplo 1**: `chown usuario:grupo archivo`  
    Cambia el propietario del archivo a "usuario" y el grupo a "grupo".

```
ls -l archivo
-rwxr--r-- 1 usuario grupo 0 date archivo
```

*   **Ejemplo 2**: `chown -R usuario:grupo /directorio`  
    Cambia recursivamente el propietario y el grupo de todos los archivos y subdirectorios en "/directorio".

```
ls -l /directorio
drwxr-xr-x 1 usuario grupo 0 date directorio
```

## chgrp (cambiar el grupo de un archivo)

El comando `chgrp` cambia el grupo al que pertenece un archivo o directorio.

*   **Ejemplo 1**: `chgrp nombre_grupo archivo`  
    Cambia el grupo del archivo a "nombre\_grupo".

```
ls -l archivo
-rwxr--r-- 1 usuario nombre_grupo 0 date archivo
```

*   **Ejemplo 2**: `chgrp -R nombre_grupo /directorio`  
    Cambia recursivamente el grupo de todos los archivos y subdirectorios en "/directorio".

```
ls -l /directorio
drwxr-xr-x 1 usuario nombre_grupo 0 date directorio
```

## umask (establecer permisos predeterminados de archivos)

El comando `umask` establece los permisos predeterminados para los archivos y directorios que se crean.

*   **Ejemplo 1**: `umask 022`  
    Establece los permisos predeterminados para archivos recién creados a 755.

```
touch nuevo_archivo
ls -l nuevo_archivo
-rwxr-xr-x 1 usuario grupo 0 date nuevo_archivo
```

*   **Ejemplo 2**: `umask 007`  
    Establece los permisos predeterminados para archivos recién creados a 770.

```
touch otro_archivo
ls -l otro_archivo
-rwxrwx--- 1 usuario grupo 0 date otro_archivo
```

*   **Ejemplo 3**: `umask -S`  
    Muestra la umask actual en notación simbólica.

```
umask -S
u=rwx,g=rx,o=rx
```

*   **Ejemplo 4**: `umask 002`  
    Establece los permisos predeterminados para archivos recién creados a 775.

```
touch nuevo_archivo
ls -l nuevo_archivo
-rwxrwxr-x 1 usuario grupo 0 date nuevo_archivo
```
## SUID (Set User ID)

El bit SUID permite que un archivo se ejecute con los permisos del propietario del archivo.

*   **Ejemplo 1**: `chmod u+s archivo`  
    Establece el bit SUID en el archivo.

```
ls -l archivo
-rwsr--r-- 1 usuario grupo 0 date archivo
```

*   **Ejemplo 2**: `ls -l archivo`  
    Muestra el bit SUID como una “s” en la posición de ejecución del propietario.

```
ls -l archivo
-rwsr--r-- 1 usuario grupo 0 date archivo
```

## SGID (Set Group ID)

El bit SGID permite que un archivo o directorio se ejecute con los permisos del grupo del archivo o directorio.

*   **Ejemplo 1**: `chmod g+s directorio`  
    Establece el bit SGID en el directorio.

```
ls -l directorio
drwxr-sr-x 1 usuario grupo 0 date directorio
```

*   **Ejemplo 2**: `ls -l directorio`  
    Muestra el bit SGID como una “s” en la posición de ejecución del grupo.

```
ls -l directorio
drwxr-sr-x 1 usuario grupo 0 date directorio
```

## Sticky bit

El bit de sticky asegura que solo el propietario del archivo o el directorio pueda eliminar o modificar archivos dentro del directorio.

*   **Ejemplo 1**: `chmod +t directorio`  
    Establece el bit de sticky en el directorio.

```
ls -ld directorio
drwxr-xr-t 1 usuario grupo 0 date directorio
```

*   **Ejemplo 2**: `ls -ld directorio`  
    Muestra el bit de sticky como una “t” en la posición de ejecución de otros.

```
ls -ld directorio
drwxr-xr-t 1 usuario grupo 0 date directorio
```
