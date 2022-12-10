# Valorant-Internal-Imgui
![image](https://user-images.githubusercontent.com/100489559/157223531-28ddf5e6-ae66-4b0d-837c-0afac311be40.png)
# Navigation

## General
* Mouse: move menu, scroll items and change values
* Arrows: navigate and change values

## Shortcuts
* Tabs and items
  * Shift + ↑: go to the first item
  * Shift + ↓: go to the last item
  * Shift + ←: previous tab
  * Shift + →: next tab
* Menu color
  * Ctrl + ←: previous menu color
  * Ctrl + →: next menu color
  * 
A DirectX 9.0c injectable DLL menu source from 2022. Unsure original creator, but has XOR String Encryption, SendToServer SDK and many other classic features


![image](https://user-images.githubusercontent.com/100489559/157223671-969a0a37-a267-4cb4-9580-191cd9c5dacd.png)
![image](https://user-images.githubusercontent.com/100489559/157223599-847a89ab-f937-48e1-8ca7-08d500795a8b.png)

Você encontrará:
m_Items.emplace(HK_TESTE1, new MenuItem("Item 1", false));

Onde **m_Items** é a lista onde armazena os itens, **HK_TESTE1** é uma enum [encontrada aqui](https://github.com/FinnProjects/MenuD3D/blob/master/Dll/Menu.h#L9)

Antes de tudo, crie um novo valor na enum, respeitando as regras de virgula

Volte para [Menu.cpp void MenuManager::CreateItems()](https://github.com/FinnProjects/MenuD3D/blob/master/Dll/Menu.cpp#L223)

Insira uma nova linha como:
m_Items.emplace(**SUAENUM**, new MenuItem("NomeDoItem", false));

**Para adicionar uma array, troque o status padrão (true, false) para {"str1", "str2", "str3"} e assim em diante, veja:**

m_Items.emplace(**SUAENUM**, new MenuItem("NomeDoItem", **{"LClick", "RClick", "Alt", "CTRL"}**));

[Exemplo simplificado](https://github.com/FinnProjects/MenuD3D/blob/master/Dll/Menu.cpp#L227)

## Como interagir com os itens do menu?

### Itens On/Off

Vá até [Menu.cpp void MenuManager::HackActions()](https://github.com/FinnProjects/MenuD3D/blob/master/Dll/Menu.cpp#L231)

Terá exemplos

Insira: 
if (GetActived(**SEUENUM**))
{
//Ação aqui
}

Quando o item for ativado no menu, ele executará a ação


### Itens tipo array:

Utilize GetArrayPos(**SUAENUM**) para obter a posição atual,

onde o primeiro item começará na posição **0**, 

ou seja, **"LClick"** = 0, **"RClick"** = 1, e assim em diante


**Lógica de uso:**

if(GetArrayPos(**SUAENUM**) == 0) //LCkick

{
//Ação Aqui
}

else if(GetArrayPos(**SUAENUM**) == 1) //RClick

{
//Ação Aqui
}

## Imagem / Animação desativadas por padrão do projeto
## Você poderá configurar para o menu utilizar imagem / animação em: 
[Header.h //Configurações](https://github.com/FinnProjects/MenuD3D/blob/master/Dll/Header.h#L74)

### Comente a definição para desativar

### OBS:

#### Caso a imagem não carregue em algumas aplicações, não force, isso trará memory leak
