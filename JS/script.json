function limpa_formulario_cep() {
    //limpar valores do formulário
    document.getElementById('logradouro').value = ("");
    document.getElementById('bairro').value = ("");
    document.getElementById('cidade').value = ("");
    document.getElementById('uf').value = ("");
};

function meu_callback(conteudo) {
    if (!("erro" in conteudo)) {
        //Atualiza os campos com valores
        document.getElementById('logradouro').value = (conteudo.logradouro);
        document.getElementById('bairro').value = (conteudo.bairro);
        document.getElementById('cidade').value = (conteudo.localidade);
        document.getElementById('uf').value = (conteudo.uf);
    }
    else {
        //cep não encontrado
        limpa_formulario_cep();
        alert("CEP não encontrado!");
    }
};

function pesquisacep(valor) {
    //nova variável cep, somente com dígitos, limpamos
    //usando regex
    var cep = valor.replace(/\D/g, '');

    //verificar se o campo cep possui um valor informado
    if (cep != "") {
        //Expressão regular (regex) para validar o CEP
        var validacep = /^[0-9]{8}$/;

        if (validacep.test(cep)) {
            //preenche os campos com "..." enquanto consulta o webservice
            document.getElementById('logradouro').value = ("...");
            document.getElementById('bairro').value = ("...");
            document.getElementById('cidade').value = ("...");
            document.getElementById('uf').value = ("...");

            //cria um elemento javascript
            var script = document.createElement('script');

            //sincroniza com o callback
            script.src = 'https://viacep.com.br/ws/' + cep + '/json/?callback=meu_callback';

            //insere script no documento e carrega o conteúdo
            document.body.appendChild(script);


        } //final do if
        else {
            //cep é inválido
            limpa_formulario_cep();
            alert("formato de cep inválido")
        }

    } //fim do if
    else {
        //cep sem valor
        limpa_formulario_cep();
    }
};
