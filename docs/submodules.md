
# Uso de Git Submodules

Os **Git Submodules** permitem incluir um repositório Git dentro de outro repositório. Isso é útil quando um projeto depende de outro projeto separado, mas você quer manter o histórico e o controle de versão independentes.

---

# 1. Adicionando um Submodule

Para adicionar um repositório como submodule dentro do seu projeto:

```bash
git submodule add <url-do-repositorio> <pasta-destino>
````

Exemplo:

```bash
git submodule add https://github.com/usuario/biblioteca.git libs/biblioteca
```

Isso irá:

* Clonar o repositório dentro da pasta especificada
* Criar o arquivo `.gitmodules`
* Registrar o submodule no repositório principal

Depois disso, faça commit:

```bash
git add .gitmodules libs/biblioteca
git commit -m "Adiciona submodule biblioteca"
```

---

# 2. Clonando um Repositório com Submodules

Quando alguém clonar o repositório principal, os submodules **não são baixados automaticamente**.

Clone usando:

```bash
git clone --recurse-submodules <url-do-repo>
```

Se já clonou sem essa opção:

```bash
git submodule init
git submodule update
```

Ou em um único comando:

```bash
git submodule update --init --recursive
```

---

# 3. Atualizando um Submodule

Para atualizar o submodule para a versão mais recente do repositório remoto:

```bash
cd caminho/do/submodule
git pull origin main
```

Depois volte ao repositório principal e registre a nova referência:

```bash
cd ..
git add caminho/do/submodule
git commit -m "Atualiza submodule"
```

---

# 4. Atualizando Todos os Submodules

Para atualizar todos os submodules de uma vez:

```bash
git submodule update --remote
```

Se houver submodules dentro de submodules:

```bash
git submodule update --remote --recursive
```

---

# 5. Mantendo um Repositório com Submodules

Boas práticas:

* Sempre fazer commit da atualização do submodule no repositório principal.
* Utilizar `--recurse-submodules` ao clonar o projeto.
* Documentar no README que o projeto utiliza submodules.
* Atualizar os submodules antes de gerar builds ou releases.

Comandos úteis:

```bash
git submodule status
git submodule update --init --recursive
git submodule update --remote
git submodule set-url libs/biblioteca <nova-url>
```

---

# 6. Estrutura do Projeto

Exemplo de estrutura:

```
meu-projeto/
│
├── src/
├── libs/
│   └── biblioteca/   (submodule)
│
├── .gitmodules
└── README.md
```

O arquivo `.gitmodules` guarda a configuração dos submodules utilizados pelo projeto.

---

