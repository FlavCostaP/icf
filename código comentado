Web VPython 3.2
### Definindo objetos iniciais: os três eixos da rampa e o objeto deslizante
rampa_h = box(pos=vector(0,40,0), axis = vector(1,1,0), size = vector(141.42,1,1)) 
rampa_y = box(pos=vector(50,40,0), height = 100)
rampa_x = box(pos=vector(0,-9.3,0), size = vector(100,1,1))
bola = sphere(pos=vector(rampa_y.pos.x, (rampa_y.height/2)+rampa_y.pos.y+2,0), radius=5, color=color.yellow)
### Definindo variáveis iniciais: theta é o ângulo chão e hipotenusa, bola.v o objeto velocidade da bola e area a área da bola
theta = atan(rampa_y.height/rampa_x.size.x)
bola.v = vector(0,0,0)
area = bola.radius**2 * 3.14
### Um slider para aumentar ou diminuir o raio da bola. Ao aumentarmos o raio, reposicionamos a bola para que seu centro esteja acima da rampa
### Também printamos o raio
def R(r):
    global area
    print('Raio:',r.value)
    bola.radius = r.value
    bola.pos.y = (rampa_y.height/2)+rampa_y.pos.y+bola.radius
    area = bola.radius**2 * 3.14
slider( bind=R, min = 1, max = 15, value = 5)
### Slider para aumentar a altura da rampa, printamos a altura para que possa ser comparado posteriormente com contas matemáticas
### Ao mudarmos a altura, reposicionamos a bola, a componente horizontal e a hipotenusa da rampa, para que elas continuem se conectando
def S(s):
    print('Altura:',s.value)
    global theta
    rampa_y.height = s.value
    bola.pos.y = (rampa_y.height/2)+rampa_y.pos.y+bola.radius
    rampa_x.pos.y = -(rampa_y.height/2) + rampa_y.pos.y
    rampa_h.size.x = (((rampa_y.height**2) + (rampa_x.size.x**2))**(1/2))
    rampa_h.axis = vector((rampa_h.size.x)*sin(atan (rampa_x.size.x/rampa_y.height)),(rampa_h.size.x)*cos(atan (rampa_x.size.x/rampa_y.height)),0) 
    theta = atan(rampa_y.height/rampa_x.size.x)
slider( bind=S, min = 0, max = 500, value = 100)
### Slider para aumentar o comprimento da rampa, printamos o comprimento
### Reposicionamos a bola no topo da rampa e as componentes Y e H (altura e hipotenusa) para que elas continuem se conectando
def V(v):
    print('Comprimento:',v.value)
    global theta
    rampa_x.size.x = v.value
    bola.pos.x = rampa_y.pos.x
    rampa_y.pos.x = (rampa_x.size.x/2) + rampa_x.pos.x
    rampa_h.size.x = (((rampa_y.height**2) + (rampa_x.size.x**2))**(1/2))
    rampa_h.axis = vector((rampa_h.size.x)*sin(atan (rampa_x.size.x/rampa_y.height)),(rampa_h.size.x)*cos(atan (rampa_x.size.x/rampa_y.height)),0)
    theta = atan(rampa_y.height/rampa_x.size.x)
slider( bind=V, min = 0, max = 500, value = 100)

### Definindo a variável começar como False
começar = False

### Botão que irá mudar a variável começar, caso esta seja False, irá se tornar True; caso esteja True, tornará False
def B(b):
    global começar
    começar = not começar
    if começar == True:
        b.text = 'Pausar'
    elif começar == False:
        b.text = 'Começar'
    #print('Posição:',bola.pos)
button( bind=B, text='Começar',pos = scene.title_anchor )
### Botão que irá reposicionar a bola no topo da rampa e reiniciar sua velocidade para 0
def P(p):
    bola.pos.x = rampa_y.pos.x
    bola.pos.y = (rampa_y.height/2)+rampa_y.pos.y+bola.radius
    bola.v = vector(0,0,0)
button( bind=P, text='Recomeçar',pos = scene.title_anchor )

### Constantes que o usuário deverá colocar
### NÃO DEVE-SE USAR VÍRGULA E SIM PONTO PARA INDICAR CASA DECIMAL
g = float(input('Dê o valor da aceleração vertical para baixo:'))
m = float(input('Dê o valor da massa da bola (maior do que 0):'))
k = float(input('Dê o valor da constante de resistência do ar'))

### Loop para funcionamento da física, caso começar == True ele funciona
### Nesse loop atualizaremos a posição da bola, a aceleração e sua posição
### Printamos a velocidade a cada momento e caso a bola toque o "piso", sua velocidade se torna 0 e a aceleração também
while True:
    rate(100)
    if começar == True:
        dt = 0.05
        if bola.pos.y>=rampa_x.pos.y+bola.radius:
            far = ((1/2)*k*area*bola.v*mag(bola.v)*0.2)
            bola.f = norm(rampa_h.axis) * (m*-g*sin(theta)/m) - (far/m)
            bola.v += bola.f *dt
            bola.pos += bola.v *dt
            print('Velocidade:', mag(bola.v))
        elif bola.pos.y <= rampa_x.pos.y:
            bola.f = vector(0,0,0)
            bola.v = vector(0,0,0)
