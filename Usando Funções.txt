CREATE OR REPLACE FUNCTION obter_descricao_segmercado
    (p_id IN segmercado.id%type)
    RETURN segmercado.descricao%type
IS
    v_descricao segmercado.descricao%type;
BEGIN
    --select do plsql só retorno uma unica linha ou coluna
    SELECT descricao INTO v_descricao
        FROM segmercado
        WHERE id = p_id;
    RETURN v_descricao;
END;



/*executando a função usando comandos do sql developer*/
--permite a criação de uma variavel de trabalho dentro do plsql
VARIABLE g_descricao varchar2(100)

/*comando execute faz referencia a variavel 
mais comando de atribuição fazendo referencia a função,
isso ira retornar o conteudo da descrição com id = 1*/
EXECUTE :g_descricao := obter_descricao_segmercado(1)

--mostra o conteudo na tela
PRINT g_descricao


/*chamando a função dentro de um comando plsql*/
SET SERVEROUTPUT ON
DECLARE
    v_descricao segmercado.descricao%type;
BEGIN
    v_descricao := obter_descricao_segmercado(2);
    dbms_output.put_line('Descricao: ' || v_descricao);
END;