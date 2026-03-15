# Actividad Evaluativa: Validación de XML con XSD y Expresiones Regulares

## Archivos Incluidos
* `usuarios.xml`: Documento XML con los datos de usuarios registrados en una aplicación web.
* `usuarios.xsd`: Esquema XML que valida la estructura y los datos del documento XML.

## Restricciones y Expresiones Regulares Utilizadas

Se han aplicado restricciones sobre los elementos simples utilizando la etiqueta `<xs:restriction>` y el atributo `<xs:pattern>` dentro del XSD.

1. **Email (`email`)**: 
   * **RegEx**: `^\S+@\S+\.\S+$`
   * **Justificación**: Asegura que la cadena contenga caracteres que no sean espacios en blanco (`\S+`), seguidos de una arroba `@`, más caracteres sin espacios, un punto `\.` y finalmente el dominio.

2. **Teléfono (`telefono`)**:
   * **RegEx**: `^[0-9]{3}[\s][0-9]{3}[\s][0-9]{3}$`
   * **Justificación**: Formato oficial para números españoles separado por espacios (ej. 954 654 321), donde se exigen bloques de 3 dígitos `[0-9]{3}` separados por el carácter de espacio en blanco `[\s]`.

3. **Código Postal (`codigoPostal`)**:
   * **RegEx**: `^[0-9]{5}$`
   * **Justificación**: En España, la codificación postal utiliza exactamente 5 dígitos numéricos. Se utiliza el cuantificador `{5}` para asegurar esta longitud exacta.

4. **Nombre de Usuario (`nombreUsuario`)**:
   * **RegEx**: `^[a-z][a-zA-Z0-9]*$`
   * **Justificación**: Obliga a que el primer carácter sea una letra minúscula `[a-z]`. El resto de la cadena puede contener cualquier número de caracteres alfanuméricos usando el comodín de repetición `*`.

5. **Contraseña (`contrasena`)**:
   * **RegEx**: `[a-zA-Z0-9!@#$%\^&amp;/\-?*_]+`
   * **Justificación**: Permite caracteres alfanuméricos y símbolos, escapando el ampersand como &amp; y el guion como \- por sintaxis XML. Se omiten los anclajes ^ y $ ya que en XSD la validación es absoluta por defecto.