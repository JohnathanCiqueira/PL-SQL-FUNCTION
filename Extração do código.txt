CREATE OR REPLACE FUNCTION categoria_cliente
    (p_faturamento_previsto IN cliente.faturamento_previsto%type)
    RETURN cliente.categoria%type

IS

BEGIN

    IF p_faturamento_previsto < 10000 THEN
       RETURN 'PEQUENO';
    ELSIF  p_faturamento_previsto < 50000 THEN
      RETURN 'MEDIO';
    ELSIF  p_faturamento_previsto < 100000 THEN
       RETURN 'MEDIO GRANDE';
    ELSE
       RETURN 'GRANDE';
    END IF;
END;

EXECUTE INCLUIR_CLIENTE (2, 'SUPERMERCADO IJK', '67890', NULL, 90000);

SELECT * FROM CLIENTE
