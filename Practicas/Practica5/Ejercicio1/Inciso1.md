# Inciso 1(Corregido)

```ada
TASK TYPE AUTO;

TASK TYPE CAMIONETA;

TASK TYPE CAMION;

TASK PUENTE IS
  ENTRY ENTRA_AUTO();
  ENTRY ENTRA_CAMION();
  ENTRY ENTRA_CAMIONETA();
  ENTRY SALE_AUTO();
  ENTRY SALE_CAMION();
  ENTRY SALE_CAMIONETA();
END PUENTE;

TASK BODY AUTO IS
  PUENTE.ENTRA_AUTO();
  PUENTE.SALE_AUTO();
END AUTO;

TASK BODY CAMION IS
  PUENTE.ENTRA_CAMION();
  PUENTE.SALE_CAMION();
END CAMION;

TASK BODY CAMIONETA IS
  PUENTE.ENTRA_CAMIONETA();
  PUENTE.SALE_CAMIONETA();
END CAMIONETA;

TASK BODY PUENTE IS
  PESO_AUTOS, PESO_CAMIONETAS, PESO_CAMION: INTEGER := 0;
  WHILE(TRUE)LOOP
    SELECT
      WHEN ((PESO_AUTOS + PESO_CAMIONETAS + PESO_CAMION + 1) <= 5) ACCEPT ENTRA_AUTO() IS
        PESO_AUTOS := PESO_AUTOS + 1;
      END ENTRA_AUTO;
    OR
      WHEN ((PESO_AUTOS + PESO_CAMIONETAS + PESO_CAMION + 2) <= 5) ACCEPT ENTRA_CAMIONETA() IS
        PESO_CAMIONETAS := PESO_CAMIONETAS + 2;
      END ENTRA_CAMIONETA;
    OR
      WHEN ((PESO_AUTOS + PESO_CAMIONETAS + PESO_CAMION + 3) <= 5) ACCEPT ENTRA_CAMION() IS
        PESO_CAMION := PESO_CAMION + 3;
      END ENTRA_CAMION;
    OR
      ACCEPT SALE_AUTO() IS
        PESO_AUTOS := PESO_AUTOS - 1;
      END SALE_AUTO;
    OR
      ACCEPT SALE_CAMIONETA() IS
        PESO_CAMIONETAS := PESO_CAMIONETAS - 2;
      END SALE_CAMIONETA;
    OR
      ACCEPT SALE_CAMION() IS
        PESO_CAMION := PESO_CAMION - 3;
      END SALE_CAMION;
  END LOOP;
END PUENTE;

VAR
  AUTOS = ARRAY(1..A) OF AUTO;
  CAMIONETAS = ARRAY(1..B) OF CAMIONETA;
  CAMIONES = ARRAY(1..C) OF CAMION;
```
