No JS, eu começo fazendo as relações de acordo com as ID's dadas no html. Que são:

let sliderElement = document.querySelector("#slider");
let buttonElement = document.querySelector("#button");

let sizePassword = document.querySelector("#valor");
let password = document.querySelector("#password");

let containerPassword = document.querySelector("#container-password");

Fiz um comando para os possíveis caracteres que a senha vai poder ter e também para ela começar vazia:

let charset = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#";
let novaSenha = "";

Código para fazer o slider funcionar, mostrando os números e a função que vai pegar o valor do tamanho da senha selecionada que foi colocada no html (6-18):

sizePassword.innerHTML = sliderElement.value;

slider.oninput = function(){
    sizePassword.innerHTML = this.value;
}

Função que faz o botão de gerar a senha funcionar, onde ele vai pegar os caracteres de forma aleatória até chegar na quantidade que foi pedida:

function generatePassword(){
    
    let pass = "";

    for(let i = 0, n = charset.length; i < sliderElement.value; ++i){
        pass += charset.charAt(Math.floor(Math.random() * n));
}

Fazendo a senha aparecer na tela quando clicar no botão de gerar: 

containerPassword.classList.remove("hide");
password.innerHTML = pass;
novaSenha = pass;

E por último, criando uma função que vai permitir que a senha dada seja copiada apenas clicando, também mostrando um alert avisando que copiou com sucesso:

function copyPassword(){
    navigator.clipboard.writeText(novaSenha).innerHTML;
    alert("Senha copiada com sucesso!")
}


