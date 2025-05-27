# automacoes-python
Automação de Tarefas com Python - Semana 1

semana1/exemplo_01_listar_arquivos.py

import os

pasta = "downloads_simulado"
os.makedirs(pasta, exist_ok=True)

# Criando arquivos simulados
arquivos = [
    "foto.jpg",
    "documento.pdf",
    "video.mp4",
    "arquivo.zip",
    "tabela.xlsx",
    "musica.mp3"
]

for nome in arquivos:
    with open(os.path.join(pasta, nome), "w") as f:
        f.write("Conteúdo de exemplo")

# Listar arquivos
print(f"Arquivos na pasta '{pasta}':")
for nome in os.listdir(pasta):
    print(f"- {nome}")





# automacoes-python
Automação de Tarefas com Python - Semana 1

semana1/exemplo_01_listar_arquivos.py

import os

pasta = "downloads_simulado"
os.makedirs(pasta, exist_ok=True)

# Criando arquivos simulados
arquivos = [
    "foto.jpg",
    "documento.pdf",
    "video.mp4",
    "arquivo.zip",
    "tabela.xlsx",
    "musica.mp3"
]

for nome in arquivos:
    with open(os.path.join(pasta, nome), "w") as f:
        f.write("Conteúdo de exemplo")

# Listar arquivos
print(f"Arquivos na pasta '{pasta}':")
for nome in os.listdir(pasta):
    print(f"- {nome}")
