---
title: Что такое SOLID? Какие из принципов SOLID нельзя реализовать в функциональном компоненте?
draft: false
tags:
  - ООП
  - SOLID
info:
  - https://habr.com/ru/companies/ruvds/articles/428079/
  - https://www.youtube.com/watch?v=A6wEkG4B38E&list=PLNkWIWHIRwMGlOBjDYTeqnNcuZ2cH1_7-
---
*`SOLID`* - это аббревиатура, которая описывает *пять принципов объектно-ориентированного программирования, которые помогают создавать более гибкие и расширяемые программы.* Каждая буква в аббревиатуре SOLID представляет собой один из этих принципов:

### 1. *`S` - Принцип единственной ответственности*

Каждый *класс* должен иметь только одну ответственность, т.е. он *должен выполнять только одну задачу*.

```jsx
import React from 'react';

// Компонент, отображающий список пользователей
function UserList({ users }) {
  return (
    <div>
      <h1>User List</h1>
      <ul>
        {users.map(user => (
          <li key={user.id}>{user.name}</li>
        ))}
      </ul>
    </div>
  );
}

export default UserList;
```

В этом примере `UserList` компонент отвечает только за отображение списка пользователей. Он принимает массив `users` в качестве пропсов и отображает их имена в виде списка

### 2.  *`O` - Принцип открытости/закрытости*

*Классы должны быть открыты для расширения, но закрыты для модификации.* Это означает, что вы можете добавлять новую функциональность в программу, не изменяя существующий код.

* **наследование**

```jsx
import React from 'react';

// Базовый компонент
class BaseComponent extends React.Component {
  // Общая логика и состояние
}

// Компонент-наследник, расширяющий BaseComponent
class ExtendedComponent extends BaseComponent {
  // Дополнительная логика и состояние
}
```

* **композиция**

```jsx
import React from 'react';

// Компонент, использующий другие компоненты
class CompositeComponent extends React.Component {
  render() {
    return (
      <div>
        <Header />
        <Content />
        <Footer />
      </div>
    );
  }
}

// Компоненты, которые используются внутри CompositeComponent
class Header extends React.Component {
  // ...
}

class Content extends React.Component {
  // ...
}

class Footer extends React.Component {
  // ...
}
```

### 3. *`L` - Принцип подстановки Барбары Лисков* 

*Объекты должны быть заменяемыми на экземпляры своих подтипов без изменения правильности программы.* То есть, если у вас есть класс-родитель и класс-наследник, то объекты класса-наследника должны использоваться везде, где используются объекты класса-родителя.

```jsx
import React from 'react';

// Базовый компонент
class BaseComponent extends React.Component {
  render() {
    return <div>{this.getDisplayText()}</div>;
  }

  getDisplayText() {
    return 'Base Component';
  }
}

// Подкласс, расширяющий BaseComponent
class SubComponent extends BaseComponent {
  getDisplayText() {
    return 'Sub Component';
  }
}

// Использование компонентов
function App() {
  return (
    <div>
      <BaseComponent />
      <SubComponent />
    </div>
  );
}

export default App;
```

### 4. *`I` - Принцип разделения интерфейса* 

*Клиенты не должны зависеть от методов, которые они не используют.* Вместо этого интерфейсы должны быть разделены на более мелкие, чтобы клиенты могли использовать только те методы, которые им нужны.

```jsx
import React from 'react';

// Интерфейс для компонента отображения данных
interface IDataDisplay {
  data: any;
}

// Компонент, отображающий список пользователей
class UserList extends React.Component<IDataDisplay> {
  render() {
    const { data } = this.props;
    return (
      <div>
        <h1>User List</h1>
        <ul>
          {data.map((user: any) => (
            <li key={user.id}>{user.name}</li>
          ))}
        </ul>
      </div>
    );
  }
}

// Компонент, отображающий одного пользователя
class UserDetails extends React.Component<IDataDisplay> {
  render() {
    const { data } = this.props;
    return (
      <div>
        <h1>User Details</h1>
        <p>Name: {data.name}</p>
        <p>Email: {data.email}</p>
      </div>
    );
  }
}

// Использование компонентов
function App() {
  const users = [
    { id: 1, name: 'John Doe', email: 'john@example.com' },
    { id: 2, name: 'Jane Smith', email: 'jane@example.com' },
  ];

  return (
    <div>
      <UserList data={users} />
      <UserDetails data={users[0]} />
    </div>
  );
}

export default App;
```

### 5. *`D` - Принцип инверсии зависимостей* 

*Модули верхнего уровня не должны зависеть от модулей нижнего уровня.* Вместо этого они должны зависеть от абстракций, а не от конкретных реализаций.

```jsx
import React from 'react';

// Интерфейс для зависимости
interface IDataService {
  fetchData(): Promise<any>;
}

// Конкретная реализация зависимости
class ApiService implements IDataService {
  fetchData(): Promise<any> {
    // Здесь может быть реализация запроса к API
    return Promise.resolve(/* Результат запроса */);
  }
}

// Компонент, использующий зависимость
class DataComponent extends React.Component {
  private dataService: IDataService;

  constructor(props: any) {
    super(props);
    this.dataService = new ApiService(); // Создание конкретной реализации зависимости
  }

  async componentDidMount() {
    const data = await this.dataService.fetchData();
    // Делаем что-то с полученными данными
  }

  render() {
    // Рендер компонента
  }
}

// Использование компонента
function App() {
  return (
    <div>
      <DataComponent />
    </div>
  );
}

export default App;
```

### Какие из принципов SOLID нельзя реализовать в функциональном компоненте?

В функциональных компонентах в React, которые используют хуки, некоторые из принципов SOLID могут быть более сложными или невозможными для строгой реализации. Вот несколько примеров:

1. *Принцип единственной ответственности (`Single Responsibility Principle, SRP`):* Функциональные компоненты в React обычно служат для отображения интерфейса и управления состоянием компонента. В них может быть несколько ответственностей, таких как обработка событий, получение данных и рендеринг. Однако, вы можете стараться разбивать функциональные компоненты на более мелкие, чтобы каждая функция была ответственна только за одну конкретную задачу.
    
2. *Принцип открытости/закрытости (`Open/Closed Principle, OCP`):* В функциональных компонентах может быть сложнее соблюдать этот принцип, особенно если требуется изменять поведение компонента через пропсы. Функциональные компоненты обычно более открыты для изменений, так как вы можете добавлять новые пропсы или изменять логику напрямую внутри компонента. Однако, вы можете стараться создавать компоненты с ясно определенными интерфейсами и использовать композицию и наследование, чтобы легко расширять функциональность компонентов.
    
3. *Принцип подстановки Барбары Лисков (`Liskov Substitution Principle, LSP`):* В функциональных компонентах в React, основанных на хуках, наследование не используется, а подклассы не создаются. Вместо этого, функциональные компоненты могут использовать композицию и переиспользование хуков для достижения поведения, аналогичного подклассам. Несмотря на это, принцип LSP остается актуальным в отношении заменяемости компонентов и сохранения ожидаемого поведения при замене одного компонента другим.

___

 [[200 Браузерное окружение|Назад]]