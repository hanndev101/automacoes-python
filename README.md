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





semana1/exercicio_01_filtrar_pdfs.py

import os

pasta = "downloads_simulado"

print(f"Arquivos .pdf na pasta '{pasta}':")
for nome in os.listdir(pasta):
    if nome.endswith(".pdf"):
        print(f"- {nome}")



semana1/desafio_01_subpastas.py

import os

base_dir = "downloads_baguncado"

subpastas = ["imagens", "documentos", "musicas", "compactados"]
arquivos = {
    "imagens": ["foto.jpg", "logo.png"],
    "documentos": ["relatorio.pdf", "anotacoes.txt"],
    "musicas": ["trilha.mp3"],
    "compactados": ["backup.zip"]
}

# Criar estrutura
for pasta in subpastas:
    caminho = os.path.join(base_dir, pasta)
    os.makedirs(caminho, exist_ok=True)
    for nome in arquivos[pasta]:
        with open(os.path.join(caminho, nome), "w") as f:
            f.write("Arquivo simulado.")

# Listar arquivos em subpastas
print(f"Arquivos encontrados dentro de '{base_dir}':")
for raiz, _, arquivos_encontrados in os.walk(base_dir):
    for nome in arquivos_encontrados:
        print(os.path.join(raiz, nome))



semana1/projeto_01_organizador.py

import os
import shutil

pasta_base = "downloads_baguncado"

for raiz, _, arquivos in os.walk(pasta_base):
    for nome in arquivos:
        caminho_origem = os.path.join(raiz, nome)
        extensao = os.path.splitext(nome)[1][1:]  # sem o ponto
        if not extensao:
            extensao = "outros"
        pasta_destino = os.path.join(pasta_base, extensao)
        os.makedirs(pasta_destino, exist_ok=True)
        shutil.move(caminho_origem, os.path.join(pasta_destino, nome))

print("📂 Organização concluída com sucesso!")



semana1/projeto_02_contador_tipos.py

import os
from collections import defaultdict

pasta_base = "downloads_baguncado"
contador = defaultdict(int)

for raiz, _, arquivos in os.walk(pasta_base):
    for nome in arquivos:
        extensao = os.path.splitext(nome)[1]
        contador[extensao] += 1

print("📊 Contagem de arquivos por tipo:")
for ext, qtd in contador.items():
    print(f"{ext}: {qtd} arquivo(s)")



semana1/projeto_03_remocao_txt.py

import os

pasta_base = "downloads_baguncado"
tipo_remover = ".txt"
removidos = 0

for raiz, _, arquivos in os.walk(pasta_base):
    for nome in arquivos:
        if nome.endswith(tipo_remover):
            caminho = os.path.join(raiz, nome)
            os.remove(caminho)
            removidos += 1

print(f"🗑️ Arquivos '{tipo_remover}' removidos: {removidos}")



semana1/projeto_04_backup.py

import os
import shutil

pasta_base = "downloads_baguncado"
backup_dir = "backup_downloads"
os.makedirs(backup_dir, exist_ok=True)
copiados = 0

for raiz, _, arquivos in os.walk(pasta_base):
    for nome in arquivos:
        origem = os.path.join(raiz, nome)
        rel_path = os.path.relpath(raiz, pasta_base)
        destino_pasta = os.path.join(backup_dir, rel_path)
        os.makedirs(destino_pasta, exist_ok=True)
        destino = os.path.join(destino_pasta, nome)
        shutil.copy2(origem, destino)
        copiados += 1

print(f"📁 Arquivos copiados para backup: {copiados}")
