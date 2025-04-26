Louie Nery Silva UC24101358
João Filipe Alves de Albuquerque UC24102128
Mateus Henrique Lacerda Lopes UC24102584
Guilherme Souza Rocha UC24101057

# NestJS: Criando uma API REST

## Introdução
- Demonstração de como criar uma API REST usando **NestJS** de forma prática e organizada.
- Exemplo prático: API para gerenciamento de uma aplicação de **Delivery** (clientes, produtos, pedidos, endereços).
- O NestJS oferece estrutura robusta com **TypeScript**, **ESLint** e **Jest** integrados.

---

## Criando o projeto
- Comando inicial: `nest new nestJS`
- Gerenciador de pacotes: **npm**
- Instalação de pacotes adicionais:
  - `sqlite3`, `typeorm`, `@nestjs/typeorm` (banco de dados)
  - `class-validator`, `class-transformer` (validação)

---

## Criando a API com o gerador de código
- Geração de recurso: `nest g resource <nome-do-recurso>`
- Tipo: **REST API**
- Estrutura gerada automaticamente:
  - Controllers
  - Services
  - DTOs
  - Entities

---

## Validação de dados
- **DTOs** usados:
  - `CreateClienteDto`, `UpdateProdutoDto`, `CreatePedidoDto`, etc.
- Validadores:
  - `@IsString`, `@IsEmail`, `@IsNumber`, `@IsDateString`
- Ativação da validação global em `main.ts` usando `ValidationPipe`.

![image](https://github.com/user-attachments/assets/412c9698-8a04-4b10-9ffc-6ca08049205b)
![image](https://github.com/user-attachments/assets/27c0b284-57cb-495d-aabf-3a1bf57606ea)
![image](https://github.com/user-attachments/assets/fc9dfe55-bca4-471d-b2a9-0825a1b78873)

## TypeORM e SQLite
- Configuração do TypeORM no `AppModule` (`TypeOrmModule.forRoot`).
- Banco de dados utilizado: **SQLite** (`db.sqlite`).
- Entidades criadas para cada recurso:
  - Definidas usando `@Entity`, `@PrimaryGeneratedColumn`, `@Column`.

![image](https://github.com/user-attachments/assets/da860f29-15e0-497b-8bcd-efcb480cd567)
![image](https://github.com/user-attachments/assets/f29f4596-9d42-4965-b2bc-8d30201ddeb7)
![image](https://github.com/user-attachments/assets/b68aa5e4-2fc3-4684-a86e-e413574358e8)
![image](https://github.com/user-attachments/assets/76c24c14-cb05-4827-b568-34cd73dc2d38)


## Injeção de dependência
- Uso de `@InjectRepository` para acessar repositórios nas services.
- Controllers injetam services via construtor.
- Dependências gerenciadas automaticamente pelo NestJS com `@Injectable`.
  
![image](https://github.com/user-attachments/assets/f2d493e2-76aa-423d-8776-29f25263f585)

## Lógica na Service
- Toda a lógica de negócio fica concentrada nas classes de service.
- Implementação dos métodos principais:
  - `create()`, `findAll()`, `findOne()`, `update()`, `remove()`
- Tratamento de erros utilizando `NotFoundException`, `HttpException`, etc.

![image](https://github.com/user-attachments/assets/25135786-c2ed-4ba9-8159-01852b2ba89b)

## Bônus: Boas práticas REST
- Retorno de códigos HTTP apropriados:
- Separação de responsabilidades:
  - Controllers cuidam das rotas.
  - Services cuidam da lógica de negócio.
- Uso consistente de DTOs para validação de entrada e saída.

![image](https://github.com/user-attachments/assets/7089dd10-f628-48c3-beca-4a3bad3b2d45)

## Próximos passos
- Implementar autenticação e autorização (exemplo: JWT).
- Adicionar testes unitários e testes de integração.
- Migrar o banco de dados para uma solução de produção (PostgreSQL).
- Documentar a API usando Swagger.

---

## Desafio!
- Criar um novo módulo chamado **cupom** com os campos:
  - `codigo` (string)
  - `desconto` (number)
  - `ativo` (boolean)
- Implementar o CRUD completo.
- Validar dados usando DTOs.
- Relacionar `cupom` com `pedido` (um cupom pode ser aplicado a um pedido).
