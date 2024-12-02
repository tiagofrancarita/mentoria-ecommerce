# E-commerce Application 🛒

Um sistema de e-commerce desenvolvido com **Java 17**, **Spring Boot**, e **MySQL**, projetado para ser escalável, modular e fácil de manter.

---

## **Recursos do Projeto**

### **1. Cadastro de Pessoa**
- Permite o registro de uma pessoa classificada como **Consumidor** ou **Vendedor**.
- **Campos obrigatórios:**
  - Nome Completo: Nome completo da pessoa.
  - CPF: Número único (validado e armazenado de forma segura).
  - Data de Nascimento: Validada para impedir registros de menores de idade (se aplicável).
  - Email: Verificado por validação.
  - Data de Cadastro: Preenchida automaticamente pelo sistema.
  - Perfil: Consumidor ou Vendedor.
  - Data Expiração da Senha: Calculada automaticamente (90 dias após cadastro).
  - Usuário Bloqueado: Indica se o usuário está bloqueado, inicialmente `false`.
  - Usuário Ativo: Indica se o usuário está ativo ou inativo, permitindo manter o histórico.

---

### **2. Cadastro de Endereço**
- Cada pessoa pode ter múltiplos endereços associados.
- **Campos obrigatórios:**
  - Logradouro
  - Número
  - Bairro
  - Cidade
  - Estado
  - CEP
  - Ponto de Referência (opcional)
- **Funcionalidades:**
  - Busca automática via API externa (ex.: ViaCEP) para preencher automaticamente campos como Logradouro, Bairro, Cidade e Estado.
  - Apenas campos como Número, Complemento e Ponto de Referência precisam ser preenchidos manualmente.

---

### **3. Cadastro de Login**
- Gera automaticamente credenciais de acesso seguras.
- **Campos obrigatórios:**
  - **Username:** Gerado automaticamente como `primeironome.sobrenome` (exemplo: `tiago.rita`). Caso o username já exista, é feita uma nova concatenação (exemplo: `tiago.santa`).
  - **Senha:** Gerada automaticamente com as seguintes regras:
    - Entre 8 e 30 caracteres.
    - Deve conter pelo menos uma letra maiúscula, uma minúscula, um número e um caractere especial.
    - Não pode conter o nome completo, partes do CPF ou data de nascimento.
  - **Troca de Senha:** Inicialmente marcado como `true`, exigindo troca no primeiro login.
  - **Expira Senha:** 90 dias após o cadastro ou última troca.
  - **Usuário Bloqueado:** Indica se o usuário está bloqueado após tentativas incorretas (inicialmente `false`).
  - **Usuário Ativo:** Indica se o login está ativo ou inativo.
- **Notificação:** O sistema envia por e-mail o **username** e a **senha gerada** para o usuário.

---

## **Tecnologias Utilizadas**

- **Java 17**
- **Spring Boot 3.x**
  - Spring Data JPA
  - Spring Security
  - Spring Web
- **Banco de dados MySQL**
- **Hibernate**
- **Maven** para gerenciamento de dependências
- **Lombok** para reduzir boilerplate
- **Swagger** para documentação de APIs
- **JUnit 5** e **Mockito** para testes
- **API ViaCEP** para consulta de endereços.

---

## **Requisitos do Sistema**

- **Java 17+**
- **Maven 3.9+**
- **MySQL 8+**
- IDE compatível (ex.: IntelliJ IDEA, Eclipse)

---

## **Configuração e Instalação**

### **1. Clone o repositório**
```bash
git clone https://github.com/seu-usuario/ecommerce-app.git
cd ecommerce-app
```

```tsql
CREATE DATABASE ecommerce_app;
```

```bash
spring.datasource.url=jdbc:mysql://localhost:3306/ecommerce_app
spring.datasource.username=seu_usuario
spring.datasource.password=sua_senha
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

### 3. Build e execução
   **1 Compile o projeto:**
```bash
mvn clean install
```

**2 Execute a aplicação:**

```bash
mvn spring-boot:run
```
---

## **Documentação da API**

**Acesse a documentação interativa gerada pelo Swagger em:**
```bash
http://localhost:8080/swagger-ui/index.html
```

---

## Estrutura do Projeto
```plaintext
src
├── main
│   ├── java
│   │   └── br.com..franca.ecommerce
│   │       ├── controller    # Controladores REST
│   │       ├── service       # Regras de negócio
│   │       ├── repository    # Repositórios JPA
│   │       ├── model         # Entidades do banco de dados
│   │       └── dto           # Objetos de transferência de dados
│   └── resources
│       ├── application.properties  # Configuração principal
│       └── schema.sql              # Script inicial do banco de dados (opcional)
└── test
    └── java
        └── br.com.franca.ecommerce   # Testes unitários e de integração
```

---

## Contribuindo
### **Contribuições são bem-vindas! Para contribuir:**

**1 - Fork este repositório.**

**2 -  Crie uma branch com a nova funcionalidade ou correção:**

```bash
git checkout -b minha-feature
```
**3 - Faça commit das alterações:**
```bash
git commit -m "Minha nova feature"
```


**4 -Envie a branch:**
```bash
git push origin minha-feature
```
**5 -Abra um Pull Request:**

---

## Licença
### **Este projeto está licenciado sob a MIT License.**

---

## Contato

* Desenvolvedor: Tiago Franca
* Email: tiagofranca.ritaa@outlook.com
* GitHub: tiagofrancarita

