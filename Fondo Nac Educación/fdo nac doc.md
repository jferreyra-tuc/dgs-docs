## Proceso de generacion de CONECTIVIDAD Y ART 11 (EXCLUIDOS)

### Educación envía 3 archivos para generar: 


![alt text](.\archivos_mail.png "Logo Title Text 1")

correspondientes a:

    1. CONECTIVIDAD (FONDO NACION)
    2. ART 11
    3. AMPLIACION HORARIA

Se realiza la carga en el sistema:

![alt text](Carga1.png "Carga de novedad seleccion tipo de liquidación" )

![alt text](Carga2.png "Carga de novedad seleccion de tipo de hoja" )

Una vez cargadas las novedades. Se deben tranformar cada hoja cargada. Luego generar la novedad de haberes. El proceso genera una hoja de tipo NOVEDAD DE HABERES de cada tipo de liquidación para armar los adicionales.

```SQL
    
    CALL USUARIO.MOD_DOCENTES.FN_TRANSFORMA_EXCLUIDOS(vNROHOJA);
        
    CALL USUARIO.MOD_DOCENTES.FN_PRINCIPAL_EXCLUIDOS(vPERIODO, -1);    
        
    call USUARIO.MOD_DOCENTES.FN_PRINCIPAL(vPERIODO, -1);
```

Se debe autorizar las hojas (WORKFLOW), generar los adicionales (NEOLIQ), transformar y liquidar (NEOLIQ).