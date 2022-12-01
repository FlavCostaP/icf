O objetivo deste código é a facilidade de acesso e utilização. Caso seja necessário, é recomendado a mudança do código para que haja um melhor aproveitamento deste. 
O funcionamento tem base na utilização de objetos e funções já inclusas no vpython, sendo assim, recomenda-se o acesso ao site glowscript.org. 
Por ser uma simulação, há um loop que atualiza as posições dos objetos, forças e velocidades em uma taxa de 100 vezes por segundo. Esse loop é o aspecto principal da lógica, uma vez que ele apresenta a física que atuará sobre a rampa.
Há o uso de sliders para que o usuário possa mudar características como: altura e comprimento da rampa e raio da bola. Os botões e sliders são widgets fornecidos pelo vpython. 

Para um bom uso, recomenda-se que a simulação seja apenas um auxiliar ao experimento.
Ao iniciar o programa, deverá ser informado unidades de aceleração, massa e coeficiente de resistência (todos como ponto flutuantes em unidades arbitrárias, sendo a massa necessariamente diferente de 0). Decidida tais constantes, o usuário poderá customizar o raio da bola e as dimensões da rampa. Para que a física comece a funcionar, basta apertar o botão "começar" e para parar, o botão "pausar"; para reposicionar a bola é necessário que pare a física e aperte o botão "recomeçar".
