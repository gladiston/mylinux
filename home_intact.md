**REAPROVEITANDO /HOME ANTES DE INSTALAÇÃO?**  
Os mais experientes em geral colocam a partição /home separada e ao reinstalar o sistema deixam essa partição sem formatação e daí reaproveitam o que já tinham nela. Essa abordagem é muito boa, contudo há um pequeno problema, porém fácil de resolver: configurações anteriores de temáticas.  
As configurações de quem logou-se antes poderiam ter fontes, temas e papéis de parede que antes existiam, mas agora que instalou o sistema não existem mais, essa configuração fica orfão dos arquivos e programas que antes existiam. Então uma boa ideia é apagar certos arquivos ocutos no perfil do usuário, são eles:  

## 1. Remover a pasta `.cache`   
A pasta `.cache` armazena caches de várias aplicações e pode ser apagada sem problemas, pois será recriada conforme o uso dos aplicativos.  

```bash
rm -rf ~/.cache
```
## 2. Remover a pasta .config  
A pasta .config contém as configurações dos aplicativos e do ambiente GNOME. Caso haja conflitos, é possível apagar ou revisar os diretórios específicos.  
```bash
rm -rf ~/.config
```
## 3. Remover a pasta .local/share  
A pasta .local/share armazena dados de uso local de alguns aplicativos. Limpar pastas específicas ou toda a pasta pode resolver problemas de compatibilidade com versões anteriores.  
```bash
rm -rf ~/.local/share
```
## 4. Remover pastas antigas do GNOME  
As pastas .gnome, .gnome2 e .gnome2_private podem estar presentes de instalações anteriores. Essas pastas não são mais usadas no GNOME moderno e podem ser apagadas.  
```bash
rm -rf ~/.gnome ~/.gnome2 ~/.gnome2_private
```
## 5. Remover o arquivo .gtkrc-2.0 
O arquivo .gtkrc-2.0 contém configurações antigas de temas GTK e pode ser removido se você estiver utilizando temas novos no GNOME moderno.  
```bash
rm ~/.gtkrc-2.0
```
## Dicas adicionais:  
Remover pastas específicas de aplicativos: Se um aplicativo específico estiver causando problemas, remova apenas as pastas correspondentes, como ~/.config ou ~/.local/share.

## Cuidado com o instalador  
Alguns instaladores quando perguntam qual conta será criada e você responder *joedoe* e já existir */home/joedoe*, irá destruir esta pasta! Assim, antes de proceder uma nova instalação renomeie a pasta existente:  
```bash
cd /home
mv johdoe johdoe.1
```
Cada instalador dá um jeito diferente para resolver o problema, por exemplo, a distro Manjaro por exemplo,simplesmente renomeia a /home antiga para @home e você nunca perde nada. O Ubuntu em versões antigas simplesmente remove a pasta anterior ao invés de reaproveitá-la. A conclusão do assunto é seguir a orientação acima quando é a primeira vez que experimenta a versão da distro escolhida.  


