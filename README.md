# controletv

        self.tamanho = 42
        self.canal = "Netflix"
        self.volume = 7
        self.marca = "TCL"

    def controle(self, comando):
        if isinstance(comando, int):
            if comando == 1:
                self.canal = "Netflix"
            elif comando == 2:
                self.canal = "Disney Plus"
            elif comando == 3:
                self.canal = "Amazon Prime"
            elif comando == 4:
                self.canal = "HBO"
            elif comando == 5:
                self.canal = "Star Plus"
            elif comando == 6:
                self.canal = "YouTube"
            elif comando == 7:
                self.canal = "Spotify"
            elif comando == 8:
                self.canal = "Premiere"
            elif comando == 9:
                self.canal = "Crunchyroll"
        elif comando.lower() == "on/off":
            self.ligada = not self.ligada
            estado = "ligada" if self.ligada else "desligada"
            print(f'TV {estado} com sucesso')
        elif comando.lower() == "volume +":
            self.volume += 1
            print('Volume aumentado com sucesso')
        elif comando.lower() == "volume -":
            self.volume -= 1
            print('Volume diminuído com sucesso')
        else:
            print(
                "Comando inválido. Digite um número de 1 a 9 para mudar o canal, 'on/off' para ligar/desligar, ou 'volume +'/'volume -' para ajustar o volume.")


# Instâncias da classe TV
tv_sala = TV(ligada=True)
tv_quarto = TV(ligada=False)

tv_sala.cor = "cinza"
tv_sala.tamanho = 55
tv_sala.canal = "Premiere"
tv_sala.volume = 22
tv_sala.marca = "Philips Ambilight"


# Função para escolher qual TV controlar
def selecionar_tv(comodo):
    if comodo.lower() == "sala":
        return tv_sala
    elif comodo.lower() == "quarto":
        return tv_quarto
    else:
        print("Cômodo não encontrado")
        return None


comodo = input('Escolha a TV (sala/quarto): ').strip().lower()
tv_selecionada = selecionar_tv(comodo)
if tv_selecionada:
    print(f'A TV está no canal {tv_selecionada.canal} e está {"ligada" if tv_selecionada.ligada else "desligada"}')
    comando = input(
        'Digite um comando (1-9 para mudar o canal, on/off para ligar/desligar, volume +, volume -): ').strip().lower()
    while comando == "on/off" and not tv_selecionada.ligada:
        tv_selecionada.controle(comando)
        comando = input(
            'Digite um comando (1-9 para mudar o canal, on/off para ligar/desligar, volume +, volume -): ').strip().lower()
    if comando.isdigit():
        comando = int(comando)
    tv_selecionada.controle(comando)
    print(
        f'Agora a TV da {comodo} está no canal {tv_selecionada.canal}, volume {tv_selecionada.volume}, estado {"ligada" if tv_selecionada.ligada else "desligada"}.')
else:
    print('Comando inválido. Digite um número entre 1 e 9, on/off, volume + ou volume -.')

# Exibição das informações das TVs
print('As características das TVs que temos são:')
print(f'A cor da TV da sala é {tv_sala.cor}')
print(f'A cor da TV do quarto é {tv_quarto.cor}')

print(f'A TV da sala está {"ligada" if tv_sala.ligada else "desligada"}')
print(f'TV do quarto está {"ligada" if tv_quarto.ligada else "desligada"}')

print(f'O tamanho da TV da sala é {tv_sala.tamanho}')
print(f'O tamanho da TV do quarto é {tv_quarto.tamanho}')
print(f'O canal padrão da TV da sala é {tv_sala.canal}')
print(f'O canal padrão da TV do quarto é {tv_quarto.canal}')
print(f'O volume definido da TV da sala é {tv_sala.volume}')
print(f'O volume definido da TV do quarto é {tv_quarto.volume}')
print(f'A marca da TV do quarto é {tv_quarto.marca}')
print(f'A marca da TV da sala é {tv_sala.marca}')
