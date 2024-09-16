# **DURANTE A INSTALAÇÃO, NÃO INSTALE NVIDIA**

Ao instalar o Ubuntu, escolha não instalar o driver proprietário NVIDIA durante a instalação, no final do processo será instalado o driver nouveau, um driver livre para as placas nVIDIA. Isso foi importante nos últimos dois anos\!  
Uma consideração especial sobre este driver é que ele é razoavelmente suficiente para resolução 1920x1080(fullhd), porém impraticável em resoluções superiores se sua intenção for aplicar dimensão das frações (125%, 150%, …) muito útil em resoluções 4K onde as letras ficam tão pequenas que é preciso aumentar a dimensão.  
Depois que o sistema estiver completamente instalado e após o boot, poderá optar por instalar o driver proprietário. Algo que precisa saber é que o driver proprietário NVIDIA não é compatível com o Wayland, se você quiser usufruir deste servidor gráfico terá de optar pelo driver intel ou noveau.
