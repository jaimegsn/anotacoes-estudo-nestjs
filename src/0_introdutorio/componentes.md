# Componentes

Em NestJS, o termo "componente" se refere a uma unidade independente e reutilizável que desempenha um papel específico na aplicação. Esses componentes podem ser Controladores (Controllers), Serviços (Services), Repositórios (Repositories) e outros.

A principal função dos componentes é fornecer uma maneira de criar, gerenciar e injetar instâncias de maneira estruturada. Essa gestão é feita pelo próprio framework, permitindo que os desenvolvedores se concentrem na lógica de negócios em vez de lidar com detalhes de gerenciamento.

Para definir e configurar componentes em NestJS, utilizamos decoradores como @Controller, @Service, @Repository e outros. Esses decoradores indicam o papel específico que o componente desempenha na arquitetura do aplicativo.

### Analogia com Spring:

Uma analogia para entender componentes em NestJS é compará-los com as classes anotadas com **`@Component`** no Spring Framework.
As classes com essa annotation são gerenciadas pelo container de inversão de controle do Spring e podem ser injetadas em outras partes do aplicativo, logo os componentes em NestJS também são gerenciados pelo framework e podem ser injetados para fornecer funcionalidades específicas em diferentes partes do aplicativo.
