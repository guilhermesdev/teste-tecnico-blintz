Com base na tela exemplo anexada, construa uma aplicação Vue.js que liste esses imóveis:

```json
[{"address":"Trump Plz #123", "city": "New Jersey", "state":"NJ", "zip":"33140", "image":"https://placeimg.com/300/200/any", "active":true}, {"address": "Truman E Rd", "city":"Kansas City", "state":"MO", "zip":"33140","image":"https://placeimg.com/300/200/any","active": true}, {"address": "Jazz Avenue 32", "city":"Salt Lake City", "state":"UT", "zip":"33333","image":"https://placeimg.com/300/200/any","active": false}]
```

- Adicione os filtros (FILTER) "active" que deve trazer os imóveis ativos e "inactive" que traga os imóveis inativos.

- Adicione ordenação (SORT) por endereço (default), cidade, estado e CEP (zip).

- Adicione um campo de busca (SEARCH) que filtre os imóveis por endereço e cidade (ex: o termo de busca 'City' encontra as 3 propriedades, enquanto 'Tru' devolve as propriedades 1 e 2, cujo endereço se inicia em 'Tru').

- O design (CSS) é importante, porém secundário. Foque em entregar uma aplicação que funcione.

- Os botões SHARE e ARCHIVE podem ser inseridos, mas não precisam de nenhuma funcionalidade.