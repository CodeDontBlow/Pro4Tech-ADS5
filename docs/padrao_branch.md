Para este projeto, adotaremos o modelo GitHub Flow com Releases para Produção quando implementado uma pipeline para a ec2 na aws.
Esta estratégia foi escolhida por combinar a agilidade e a simplicidade de uma
única branch principal com a segurança de um processo de lançamento controlado
para o ambiente de produção. O modelo se alinha perfeitamente aos requisitos de
Integração Contínua (IC) e Deploy Automático (CD) do projeto.

A filosofia é simples: a branch main representa o código mais atual e integrado,
que é continuamente entregue a um ambiente de testes (staging), enquanto o
ambiente de produção é atualizado apenas por meio de lançamentos de versões
(releases) explícitas e controladas.

### Fluxo de Trabalho

1. **Branch principal**
    - Utilizamos apenas uma branch de longa duração: `main`.
    - Ela representa sempre o estado mais estável do código.
2. **Branches de desenvolvimento**
    - Novas funcionalidades ou correções devem ser desenvolvidas em branches
    curtas, criadas a partir da `main`.
    - Nomenclatura:
        - `101-feat/nome-da-feature`
        - `202-fix/nome-do-bug`
        
        > Note que é separado por numero da `task`-`tipo_de_branch`/`nome_relacionado_ao_tipo`
        > 
3. **Pull Requests (PRs)**
    - Antes de integrar qualquer mudança à `main`, deve ser aberto um **PR**.
    - Os PRs ao serem abertos passam por revisão de código e execução automática
    de testes e build para garantir a integração do trabalho do desenvolvedor o
    quanto antes.
    - O título do PR deve conter o ID da tarefa correspondente (ex: `[PRO4-42] Implementação do módulo de chat`).