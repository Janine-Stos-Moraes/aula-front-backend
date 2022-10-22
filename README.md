document.addEventListener('DOMContentLoaded', function() {
    setInterval(function() {
        trocarTextDoTituloRandomicamente();
    }, 500);
});

function trocarTextDoTituloRandomicamente() {
    var meuTitulo = document.getElementsByClassName('meu-titulo');
    var texto = meuTitulo[0].innerHTML;

    var textos = [
        'TI 360!',
        'TI 360! Como vai você?',
        'TI 360! Como vai você? Estou bem!',
        'TI 360! Como vai você? Estou bem! E você?',
        'TI 360! Como vai você? Estou bem! E você? Estou bem também!',
        'TI 360! Como vai você? Estou bem! E você? Estou bem também! Obrigado!',
        'TI 360! Como vai você? Estou bem! E você? Estou bem também! Obrigado! E você?',
    ];

    var textoAleatorio = textos[Math.floor(Math.random() * textos.length)];

    meuTitulo[0].innerHTML = textoAleatorio;
}

function enviarFormulario() {
    var formulario = document.getElementById('ti360-cadastro');
    var dadosDoFormulario = new FormData(formulario);

    var myHeaders =new Headers();
    myHeaders.append("Content-type","aplication/json");

    fetch('http://localhost:8080/mensagens', {
        method: 'POST',
        body: JSON.stringify(Object.fromEntries(dadosDoFormulario)),
        headers:myHeaders

    }).then(function(resposta) {
        return resposta.text();
    }).then(function(erro) {
        alert(erro);
    });

    return;
}
