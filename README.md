# Automacao-utilizando-python-
# Passo a passo do projeto
# Passo 1: Entrar no sistema da empresa 
# https://dlp.hashtagtreinamentos.com/python/intensivao/login

import pyautogui
import time
import pandas as pd

# Pausa de segurança entre cada comando do pyautogui
pyautogui.PAUSE = 0.5

# abrir o navegador (chrome)
pyautogui.press("win")
pyautogui.write("chrome")
pyautogui.press("enter")

# Espera o Chrome abrir completamente antes de digitar o URL
time.sleep(2)

# entrar no link 
pyautogui.write("https://dlp.hashtagtreinamentos.com/python/intensivao/login")
pyautogui.press("enter")

# Espera o site carregar totalmente
time.sleep(3)

# Passo 2: Fazer login
# 1. Clica no campo de e-mail
pyautogui.click(x=685, y=451)

# 2. Escreve o e-mail e passa para o campo de senha
pyautogui.write("roberthmarinho117@gmail.com")
pyautogui.press("tab")

# 3. Escreve a senha e pressiona Enter diretamente para logar (evita erro de clique)
pyautogui.write("sssroberr")
pyautogui.press("enter")

# Espera o sistema carregar a tela dos produtos
time.sleep(3)

# Passo 3: Importar a base de produtos pra cadastrar
tabela = pd.read_csv(r"D:\roberth0arise\Videos\Gravações de Tela\produtos.csv")
print(tabela)

# Passo 4: Cadastrar os produtos
for linha in tabela.index:
    # Clica no primeiro campo (Código do produto)
    pyautogui.click(x=653, y=294)
    
    # Preenche todos os campos usando TAB
    pyautogui.write(str(tabela.loc[linha, "codigo"]))
    pyautogui.press("tab")
    
    pyautogui.write(str(tabela.loc[linha, "marca"]))
    pyautogui.press("tab")
    
    pyautogui.write(str(tabela.loc[linha, "tipo"]))
    pyautogui.press("tab")
    
    pyautogui.write(str(tabela.loc[linha, "categoria"]))
    pyautogui.press("tab")
    
    pyautogui.write(str(tabela.loc[linha, "preco_unitario"]))
    pyautogui.press("tab")
    
    pyautogui.write(str(tabela.loc[linha, "custo"]))
    pyautogui.press("tab")
    
    # Trata o campo de observação se não estiver vazio
    obs = tabela.loc[linha, "obs"]
    if not pd.isna(obs):
        pyautogui.write(str(obs))
        
    pyautogui.press("tab") # Passa para o botão Enviar
    pyautogui.press("enter") # Clica em Enviar
    
    # Rola a tela para cima para garatir que o topo fique visível para o próximo clique
    pyautogui.scroll(5000)
