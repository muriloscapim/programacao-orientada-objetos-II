# Pacotes

Pacotes são grupos de classes relacionadas.

Os pacotes ajudam a organizar o código e fornecem outra camada de encapsulamento. (controle de acesso)

# Pacotes e o acesso a membros

Os pacotes também participam do mecanismo de controle de acesso Java.

A visibilidade de um elemento é determinada por sua especificação de acesso **private, public, protected ou padrão** e o pacote em que ele reside.

A visibilidade de um elemento é determinada por sua visibilidade dentro de uma classe e sua visibilidade dentro de um pacote.

Se o membro de uma classe não tiver um modificador de acesso explícito, será default, poderá ser visto dentro de seu pacote, mas não fora dele. Privados para o pacote, mas públicos dentro dele.

Membros declarados como **public** podem ser vistos em todos os locais, inclusive classes e pacotes diferentes, pois não há restrição quanto ao seu uso ou acesso.

Um membro **private** só pode ser acessado por outros membros de sua classe. Ele não é afetado por sua associação a um pacote.

Um membro **protected** pode ser acessado dentro de seu pacote e por toas as subclasses, inclusive subclasses em outros pacotes.

**Uma classe tem dois níveis de acesso possíveis: padrão e público. Quando uma classe é declarada como public, pode ser acessada por qualquer código. O acesso padrão, só poderá ser acessada por um código do mesmo pacote.**

Acesso a membros de classes

| | Membro privado | Membro padrão | Membro protegido | Membro público |
| - | - | - | - | - |
| Visível dentro da mesma classe | Sim | Sim | Sim | Sim |
| Visível dentro do mesmo pacote pela subclasse | Não | Sim | Sim | Sim |
| Visível dentro do mesmo pacote por não subclasses | Não | Sim | Sim | Sim |
| Visível dentro de pacote diferente pela subclasse | Não | Não | Sim | Sim |
| Visível dentro de pacote diferente por não subclasses | Não | Não | Não | Sim |
