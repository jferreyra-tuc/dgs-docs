## Proceso de generacion de CONECTIVIDAD Y ART 11 (EXCLUIDOS)

### Educación envía 3 archivos para generar: 


![alt text](.\archivos_mail.png "Logo Title Text 1")

correspondientes a:

    1. 21 CONECTIVIDAD (Tipo 1 FONDO NACION)
    2. 30 ART 11 (Tipo 2)
    3. 26 AMPLIACION HORARIA (Tipo 3)

Se realiza la carga en el sistema:

![alt text](Carga1.png "Carga de novedad seleccion tipo de liquidación" )

![alt text](Carga2.png "Carga de novedad seleccion de tipo de hoja" )

Antes de aceptar la carga de los archivos, se debe validar que el tipo de liquidacion, ya sea FN NAC, AMPLIACION HORARIA y ART 11 corresponda al tipo de novedad, tipo 1, 2 y 3 .

Una vez cargadas las novedades. Se deben tranformar cada hoja cargada. Luego generar la novedad de haberes. El proceso genera una hoja de tipo NOVEDAD DE HABERES de cada tipo de liquidación para armar los adicionales.

```SQL
    
    CALL USUARIO.MOD_DOCENTES.FN_TRANSFORMA_EXCLUIDOS(vNROHOJA);   /* TRANSFORMAR  - PARA TODOS */

    call USUARIO.MOD_DOCENTES.GENERA_NOVEDAD_HE_DOC(vPERIODO,0 );  /* FN 151 - EXTENSION HORARIA DOCENTE - TIPO LIQ =  26 */
        
    CALL USUARIO.MOD_DOCENTES.FN_PRINCIPAL_EXCLUIDOS(vPERIODO, -1);  /* FN 152 - ART 11 - TIPO LIQ =  30 */
        
    call USUARIO.MOD_DOCENTES.FN_PRINCIPAL(vPERIODO, -1);   /* FN 150 - CONECTIVIDAD - TIPO LIQ =  21 */

```

Se debe autorizar las hojas (WORKFLOW), generar los adicionales (NEOLIQ), transformar y liquidar (NEOLIQ).
