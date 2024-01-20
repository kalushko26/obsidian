
#### 1. Что возвращает #fetch? Как получить содержимое ответа? Как обрабатывать ошибки?  
##### Кратко

Метод #fetch позволяет нам делать запросы данных с сервера с использованием #promise .
Что позволяет избегать катастрофического количества #callback 'ов.

Синтаксис:
`let promise = fetch(url, [options])`
с использованием дополнительного метода #response 
> res = await fetch(url); // обработали запрос к url
> body = await res.json(); // обработали результат

Кроме .json() есть другие функции для других типов ответа : arrayBuffer() , blob(), text(), formData()

fetch отклоняет (reject) promise , только если произошла ошибка сети (сервер недоступен);
Код ответа : 400 - клиентские ошибки, 500 - ошибка со стороны сервера

Чтобы проверить код результата , можно использовать result.status 
result.ok содержит true , если result.status содержит один из OK-статусов ( 200 -299 )

Для того, чтобы обработать ошибки можно использовать конструкцию if..else и result.status .

~~~
  onHandleSubmit = (e) => {
    e.preventDefault();
    fetch(`https://api.themoviedb.org/3/search/movie?api_key=${this.apiKey}&query=${this.state.searchMovies}`)
      .then((data) => data.json())
      .then((data) => {
        this.setState({ moviesData: [...data.results], isLoading: false });
      });
  };
~~~

##### Подробнее: [[1.4 FETCH]]

Метод #fetch() позволяет нам делать запросы, схожие с #XMLHttpRequest ( #XHR). 
Основное отличие заключается в том, что Fetch API использует [Promises (Обещания)](http://habrahabr.ru/post/209662/), 

	которые позволяют использовать более простое и чистое #API, избегать катастрофического количества callback'ов и необходимости помнить API для XMLHttpRequest.
	
Он не поддерживается старыми (можно использовать полифил), но поддерживается всеми современными браузерами.

Базовый синтаксис:
~~~
`let promise = fetch(url, [options])`
~~~
-   **`url`** – URL для отправки запроса.
-   **`options`** – дополнительные параметры: метод, заголовки и так далее
Без `options` это простой #GET -запрос, скачивающий содержимое по адресу `url`.

Процесс получения ответа обычно происходит в два этапа.

1.  #promise выполняется с объектом встроенного класса [Response](https://fetch.spec.whatwg.org/#response-class) в качестве результата, как только сервер пришлёт заголовки ответа.

	На этом этапе мы можем проверить статус #HTTP-запрос и определить, выполнился ли он успешно, а также посмотреть заголовки, но пока без тела ответа.
	Промис завершается с ошибкой, если `fetch` не смог выполнить HTTP-запрос, например при ошибке сети или если нет такого сайта. HTTP-статусы 404 и 500 не являются ошибкой.
	Мы можем увидеть #HTTP-статус в свойствах ответа:
		-   **`status`** – код статуса HTTP-запроса, например 200.
		-   **`ok`** – логическое значение: будет `true`, если код HTTP-статуса в диапазоне 200-299.

Например:
~~~
let response = await fetch(url);  

if (response.ok) { 
// если HTTP-статус в диапазоне 200-299   
// получаем тело ответа (см. про этот метод ниже)   
	let json = await response.json(); 
} else {   
	alert("Ошибка HTTP: " + response.status); 
}`
~~~

2.  Для получения тела ответа нам нужно использовать дополнительный вызов метода

	#response предоставляет несколько методов, основанных на промисах, для доступа к телу ответа в различных форматах:
		-   **`response.text()`** – читает ответ и возвращает как обычный текст,
		-   **`response.json()`** – декодирует ответ в формате JSON,
		-   **`response.formData()`** – возвращает ответ как объект `FormData` (разберём его в [следующей главе](https://learn.javascript.ru/formdata)),
		-   **`response.blob()`** – возвращает объект как [Blob](https://learn.javascript.ru/blob) (бинарные данные с типом),
		-   **`response.arrayBuffer()`** – возвращает ответ как [ArrayBuffer](https://learn.javascript.ru/arraybuffer-binary-arrays) (низкоуровневое представление бинарных данных),
		-   помимо этого, `response.body` – это объект [ReadableStream](https://streams.spec.whatwg.org/#rs-class), с помощью которого можно считывать тело запроса по частям. Мы рассмотрим и такой пример несколько позже.

Типичный запрос с помощью `fetch` состоит из двух операторов `await`:
~~~
let response = await fetch(url, options); // завершается с заголовками ответа 
let result = await response.json(); // читать тело ответа в формате JSON`
~~~
Или, без `await`:
~~~
fetch(url, options)   
	.then(response => response.json())   
	.then(result => /* обрабатываем результат */)`
~~~

#### 2. #AJAX и обращение к #API

Вы можете использовать встроенный в браузер метод [window.fetch](https://learn.javascript.ru/fetch) 

Вы можете сделать #AJAX-запрос в [`componentDidMount`](https://ru.reactjs.org/docs/react-component.html#mounting). Когда вы получите данные, вызовите `setState`, чтобы передать их компоненту.

#### 3. Функции #Lifecycle (жизненный цикл компонента и методы)

###### Зачем нужен жизненный цикл?

Жизненный цикл используется в те моменты, когда компонентам нужно выполнить код ( в какие - то определенные моменты своей жизни ) , например, перед тем, как компонент будет удалён, необходимо очистить ресурсы.

##### Методы жизненного цикла

Сначала в компоненте создаются через constructor состояния и свойства, затем React вызывает функцию render. Render возвращает дерево React-элементов, а эти элементы превращаются в DOM-элементы, которые затем добавляются в DOM-дерево на странице. Затем компонент может некоторое время обновляться.

В то время, когда компонент обновляется может произойти следующее событие:

Компонент может получить новое свойство, придётся вызвать функцию render , чтобы получить новое представление об элементах.

##### Функции жизненного цикла компонентов #Lifecycle-hooks

#componentDidMount - #React исполнит этот код, когда он отобразится на странице в первый раз.

Этапы Lifecycle:
___1 #Mointing - компонент создаётся и впервые отображается на странице 
constructor() => render() => #componentDidMount()

___2 #updates - компонент получает обновления
New Props
					=> render() => #componentDidUpdate()
setState()

___3 #unmounting - компонент не нужен и он удаляется

#compomemtWillInmount

___4 #error - компонент выходит с ошибккой, которая не была поймана
 #componentDidCatch ()

Подробнее: [Методы жизненного цикла](https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)

###### #componentDidMount ()
Когда этот элемент вызван - это значит , что DOM-элемент гарантировано находится на странице и они проинициализированы.

Он используется для иницициализации (запросы к API, асинхронное получение данных и тд)
%%Не используйте конструктор, для кода, который создаёт побочные эффекты.%%

Вы **можете сразу вызвать setState()** в `componentDidMount()`. Это вызовет дополнительный рендер перед тем, как браузер обновит экран. Гарантируется, что пользователь не увидит промежуточное состояние, даже если `render()` будет вызываться дважды. Используйте этот подход с осторожностью, он может вызвать проблемы с производительностью. В большинстве случаев начальное состояние лучше объявить в `constructor()`. Однако, это может быть необходимо для случаев, когда нужно измерить размер или положение DOM-узла, на основе которого происходит рендер. Например, для модальных окон или всплывающих подсказок.

###### #componentDidUpdate()

```
componentDidUpdate(prevProps, prevState, snapshot)
```

Он вызывается после того, как компонент обновился. А компонент обновляется после того, как получает новые свойства или #State 
Этот метод вызывается после render - в нём можно, к примеру, запрашивать новые данные для обновленных свойств.

```
componentDidUpdate(prevProps) {
  // Популярный пример (не забудьте сравнить пропсы):
  if (this.props.userID !== prevProps.userID) {
    this.fetchData(this.props.userID);
  }
```

В `componentDidUpdate()` **можно вызывать `setState()`**, однако его **необходимо обернуть в условие**, как в примере выше, чтобы не возник бесконечный цикл. Вызов `setState()` влечет за собой дополнительный рендер, который незаметен для пользователя, но может повлиять на производительность компонента. Вместо «отражения» пропсов в состоянии рекомендуется использовать пропсы напрямую. 

Подробнее о том, [почему копирование пропсов в состояние вызывает баги](https://ru.reactjs.org/blog/2018/06/07/you-probably-dont-need-derived-state.html).

В тех редких случаях когда реализован метод жизненного цикла `getSnapshotBeforeUpdate()`, его результат передаётся `componentDidUpdate()` в качестве третьего параметра `snapshot`.

> Примечание:
> `componentDidUpdate()` не вызывается (после рендера) , если [`shouldComponentUpdate()`](https://ru.reactjs.org/docs/react-component.html#shouldcomponentupdate) возвращает `false`.

###### #compomemtWillInmount ()
С помощью этого метода вызывается удаление компонента.
Метод используется для очистки ресурсов (таймеры, интервалы, запросы к серверу и др)

В момент вызова метода DOM все еще находится на странице.

**Не используйте setState()** в `componentWillUnmount()`, так как компонент никогда не рендерится повторно. После того, как экземпляр компонента будет размонтирован, он никогда не будет примонтирован снова.

###### #componentDidCatch ()
```
componentDidCatch(error, info)
```
1.  `error` — перехваченная ошибка
2.  `info` — объект с ключом `componentStack`, содержащий [информацию о компоненте, в котором произошла ошибка](https://ru.reactjs.org/docs/error-boundaries.html#component-stack-traces).

Задача этого метода отлов ошибок из функций, которые отвечают за корректный рендер компонентов. Принцип работы метода схож с try/catch , т.е ошибку отлавливает каждый блок.

Не обрабатываются ошибки в event listener ' ах и в асинхронном коде (запросы к серверу и т.п.)

```
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {
    // Обновите состояние так, чтобы следующий рендер показал запасной интерфейс.
    return { hasError: true };
  }

  componentDidCatch(error, info) {    // Пример "componentStack":    //   in ComponentThatThrows (created by App)    //   in ErrorBoundary (created by App)    //   in div (created by App)    //   in App    logComponentStackToMyService(info.componentStack);  }
  render() {
    if (this.state.hasError) {
      // Здесь можно рендерить запасной интерфейс
      return <h1>Что-то пошло не так.</h1>;
    }

    return this.props.children;
  }
}
```

Обработка ошибок в методе `componentDidCatch()` отличается между React-сборками для продакшена и разработки.

В процессе разработки ошибки будут подниматься (всплывать) наверх до объекта `window`, поэтому любой вызов `window.onerror` или `window.addEventListener('error', callback)` перехватит ошибки, которые были обработаны `componentDidCatch()`.

На продакшене, напротив, ошибки не всплывают, поэтому родительский обработчик ошибок перехватит только те ошибки, которые не были обработаны `componentDidCatch()`.

> Примечание:
> 
> В случае ошибки вы можете рендерить запасной интерфейс с помощью `componentDidCatch()`, вызвав `setState`. Однако, этот способ скоро будет считаться устаревшим. Используйте `static getDerivedStateFromError()` для рендера резервного интерфейса.

#### 4. React.Context

##### Кратко

Контекст позволяет передавать данные через дерево компонентов без необходимости передавать пропсы на промежуточных уровнях.

Для того, чтобы создать контекст, используем :

const { Provider , Consumer } = React.createService()
~~~
<Provider value={someValue}>
	.. // провайдер оборачивает часть приложения

Компонент `Provider` принимает проп `value`, который будет передан во все компоненты, использующие этот контекст и являющиеся потомками этого компонента `Provider`

*Предостережения*
</Provider>
~~~

```
<Consumer> {
	(someValue) => <MyComponent data={someValue} />

Эта функция принимает текущее значение контекста и возвращает React-компонент. Передаваемый аргумент `value` будет равно значению компонента `Provider`. 
Если такого компонента `Provider` не существует, аргумент `value` будет равен значению `defaultValue`, которое было передано в `createContext()`.

} </ Consumer>
```

 Подробнее про паттерн «_функция как дочерний компонент_» можно узнать на странице [Рендер-пропсы](https://ru.reactjs.org/docs/render-props.html).
	**рендер-проп — функция, которая сообщает компоненту что необходимо рендерить.**

##### #Context Зачем он нужен?

Контекст позволяет передавать данные через дерево компонентов без необходимости передавать пропсы на промежуточных уровнях.

Для того, чтобы создать контекст, используем:
```
const MyContext = React.createContext(defaultValue);
```

Создаёт объект `Context`. Когда React рендерит компонент, который подписан на этот объект, React получит текущее значение контекста из ближайшего подходящего `Provider` выше в дереве компонентов.

%%Аргумент `defaultValue` используется **только** в том случае, если для компонента нет подходящего `Provider` выше в дереве. Значение по умолчанию может быть полезно для тестирования компонентов в изоляции без необходимости оборачивать их. Обратите внимание: если передать `undefined` как значение `Provider`, компоненты, использующие этот контекст, не будут использовать `defaultValue`.%%

##### Context.Provider

```
<MyContext.Provider value={/* некоторое значение */}>
```

Каждый объект `Context` используется вместе с `Provider` компонентом, который позволяет дочерним компонентам, использующим этот контекст, подписаться на его изменения.

%%Компонент `Provider` принимает проп `value`, который будет передан во все компоненты, использующие этот контекст и являющиеся потомками этого компонента `Provider`. Один `Provider` может быть связан с несколькими компонентами, потребляющими контекст. Так же компоненты `Provider` могут быть вложены друг в друга, переопределяя значение контекста глубже в дереве.%%

Все потребители, которые являются потомками Provider, будут повторно рендериться, как только проп `value` у Provider изменится. Потребитель (включая [`.contextType`](https://ru.reactjs.org/docs/context.html#classcontexttype) и [`useContext`](https://ru.reactjs.org/docs/hooks-reference.html#usecontext)) перерендерится при изменении контекста, даже если его родитель, не использующий данный контекст, блокирует повторные рендеры с помощью `shouldComponentUpdate`.

Изменения определяются с помощью сравнения нового и старого значения, используя алгоритм, аналогичный [`Object.is`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object/is#Description).

> Примечание
> Способ, по которому определяются изменения, может вызвать проблемы при передаче объекта в `value`: смотрите [Предостережения](https://ru.reactjs.org/docs/context.html#caveats).

##### Class.contextType

```
class MyClass extends React.Component {
  componentDidMount() {
    let value = this.context;
    /* выполнить побочный эффект на этапе монтирования, используя значение MyContext */
  }
  componentDidUpdate() {
    let value = this.context;
    /* ... */
  }
  componentWillUnmount() {
    let value = this.context;
    /* ... */
  }
  render() {
    let value = this.context;
    /* отрендерить что-то, используя значение MyContext */
  }
}
MyClass.contextType = MyContext;
```

В свойство класса `contextType` может быть назначен объект контекста, созданный с помощью [`React.createContext()`](https://ru.reactjs.org/docs/context.html#reactcreatecontext). С помощью этого свойства вы можете использовать ближайшее и актуальное значение указанного контекста при помощи `this.context`. В этом случае вы получаете доступ к контексту, как во всех методах жизненного цикла, так и в рендер-методе.

> Примечание
> 
> Вы можете подписаться только на один контекст, используя этот API. В случае, если вам необходимо использовать больше одного, смотрите [Использование нескольких контекстов](https://ru.reactjs.org/docs/context.html#consuming-multiple-contexts).
> 
> Если вы используете экспериментальный [синтаксис публичных полей класса](https://babeljs.io/docs/plugins/transform-class-properties/), вы можете использовать **static** поле класса, чтобы инициализировать ваш `contextType`.

```
class MyClass extends React.Component {
  static contextType = MyContext;
  render() {
    let value = this.context;
    /* отрендерить что-то, используя значение MyContext */
  }
}
```

##### Context.Consumer

```
<MyContext.Consumer>
  {value => /* отрендерить что-то, используя значение контекста */}
</MyContext.Consumer>
```

`Consumer` — это React-компонент, который подписывается на изменения контекста. В свою очередь, использование этого компонента позволяет вам подписаться на контекст в [функциональном компоненте](https://ru.reactjs.org/docs/components-and-props.html#function-and-class-components).

`Consumer` принимает [функцию в качестве дочернего компонента](https://ru.reactjs.org/docs/render-props.html#using-props-other-than-render). Эта функция принимает текущее значение контекста и возвращает React-компонент. Передаваемый аргумент `value` будет равен ближайшему (вверх по дереву) значению этого контекста, а именно пропу `value` компонента `Provider`. Если такого компонента `Provider` не существует, аргумент `value` будет равен значению `defaultValue`, которое было передано в `createContext()`.

> Примечание
> 
> Подробнее про паттерн «_функция как дочерний компонент_» можно узнать на странице [Рендер-пропсы](https://ru.reactjs.org/docs/render-props.html).

##### Context.displayName

Объекту `Context` можно задать строковое свойство `displayName`. React DevTools использует это свойство при отображении контекста.

К примеру, следующий компонент будет отображаться под именем MyDisplayName в DevTools:

```
const MyContext = React.createContext(/* некоторое значение */);
MyContext.displayName = 'MyDisplayName';
<MyContext.Provider> // "MyDisplayName.Provider" в DevTools
<MyContext.Consumer> // "MyDisplayName.Consumer" в DevTools
```

##### Динамический контекст

Более сложный пример динамических значений для UI-темы:

**theme-context.js**

```
export const themes = {
  light: {
    foreground: '#000000',
    background: '#eeeeee',
  },
  dark: {
    foreground: '#ffffff',
    background: '#222222',
  },
};

export const ThemeContext = React.createContext(  themes.dark // значение по умолчанию);
```

**themed-button.js**

```
import {ThemeContext} from './theme-context';

class ThemedButton extends React.Component {
  render() {
    let props = this.props;
    let theme = this.context;    return (
      <button
        {...props}
        style={{backgroundColor: theme.background}}
      />
    );
  }
}
ThemedButton.contextType = ThemeContext;
export default ThemedButton;
```

**app.js**

```
import {ThemeContext, themes} from './theme-context';
import ThemedButton from './themed-button';

// Промежуточный компонент, который использует ThemedButton
function Toolbar(props) {
  return (
    <ThemedButton onClick={props.changeTheme}>
      Change Theme
    </ThemedButton>
  );
}

class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      theme: themes.light,
    };

    this.toggleTheme = () => {
      this.setState(state => ({
        theme:
          state.theme === themes.dark
            ? themes.light
            : themes.dark,
      }));
    };
  }

  render() {
    // ThemedButton внутри ThemeProvider использует    // значение светлой UI-темы из состояния, в то время как    // ThemedButton, который находится вне ThemeProvider,    // использует тёмную UI-тему из значения по умолчанию    return (
      <Page>
        <ThemeContext.Provider value={this.state.theme}>          <Toolbar changeTheme={this.toggleTheme} />        </ThemeContext.Provider>        <Section>
          <ThemedButton />        </Section>
      </Page>
    );
  }
}

const root = ReactDOM.createRoot(
  document.getElementById('root')
);
root.render(<App />);
```

##### Изменение контекста из вложенного компонента

Довольно часто необходимо изменить контекст из компонента, который находится где-то глубоко в дереве компонентов. В этом случае вы можете добавить в контекст функцию, которая позволит потребителям изменить значение этого контекста:

**theme-context.js**

```
// Убедитесь, что форма значения по умолчанию,
// передаваемого в createContext, совпадает с формой объекта,
// которую ожидают потребители контекста.
export const ThemeContext = React.createContext({
  theme: themes.dark,  toggleTheme: () => {},});
```

**theme-toggler-button.js**

```
import {ThemeContext} from './theme-context';

function ThemeTogglerButton() {
  // ThemeTogglerButton получает из контекста  // не только значение UI-темы, но и функцию toggleTheme.  return (
    <ThemeContext.Consumer>
      {({theme, toggleTheme}) => (        <button
          onClick={toggleTheme}
          style={{backgroundColor: theme.background}}>
          Toggle Theme
        </button>
      )}
    </ThemeContext.Consumer>
  );
}

export default ThemeTogglerButton;
```

**app.js**

```
import {ThemeContext, themes} from './theme-context';
import ThemeTogglerButton from './theme-toggler-button';

class App extends React.Component {
  constructor(props) {
    super(props);

    this.toggleTheme = () => {
      this.setState(state => ({
        theme:
          state.theme === themes.dark
            ? themes.light
            : themes.dark,
      }));
    };

    // Состояние хранит функцию для обновления контекста,    // которая будет также передана в Provider-компонент.    this.state = {
      theme: themes.light,
      toggleTheme: this.toggleTheme,    };
  }

  render() {
    // Всё состояние передаётся в качестве значения контекста    return (
      <ThemeContext.Provider value={this.state}>        <Content />
      </ThemeContext.Provider>
    );
  }
}

function Content() {
  return (
    <div>
      <ThemeTogglerButton />
    </div>
  );
}

const root = ReactDOM.createRoot(
  document.getElementById('root')
);
root.render(<App />);
```

##### Использование нескольких контекстов

Чтобы последующие рендеры (связанные с контекстом) были быстрыми, React делает каждого потребителя контекста отдельным компонентом в дереве.

```
// Контекст UI-темы, со светлым значением по умолчанию
const ThemeContext = React.createContext('light');

// Контекст активного пользователя
const UserContext = React.createContext({
  name: 'Guest',
});

class App extends React.Component {
  render() {
    const {signedInUser, theme} = this.props;

    // Компонент App, который предоставляет начальные значения контекстов
    return (
      <ThemeContext.Provider value={theme}>        <UserContext.Provider value={signedInUser}>          <Layout />
        </UserContext.Provider>      </ThemeContext.Provider>    );
  }
}

function Layout() {
  return (
    <div>
      <Sidebar />
      <Content />
    </div>
  );
}

// Компонент, который может использовать несколько контекстов
function Content() {
  return (
    <ThemeContext.Consumer>      {theme => (        <UserContext.Consumer>          {user => (            <ProfilePage user={user} theme={theme} />          )}        </UserContext.Consumer>      )}    </ThemeContext.Consumer>  );
}
```

Если два или более значений контекста часто используются вместе, возможно, вам стоит рассмотреть создание отдельного компонента, который будет передавать оба значения дочерним компонентам с помощью паттерна «рендер-пропс».

##### Предостережения

Контекст использует сравнение по ссылкам, чтобы определить, когда запускать последующий рендер. Из-за этого существуют некоторые подводные камни, например, случайные повторные рендеры потребителей, при перерендере родителя Provider-компонента. В следующем примере будет происходить повторный рендер потребителя каждый повторный рендер Provider-компонента, потому что новый объект, передаваемый в `value`, будет создаваться каждый раз:

```
class App extends React.Component {
  render() {
    return (
      <MyContext.Provider value={{something: 'something'}}>        <Toolbar />
      </MyContext.Provider>
    );
  }
}
```

Один из вариантов решения этой проблемы — хранение этого объекта в состоянии родительского компонента:

```
class App extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: {something: 'something'},    };
  }

  render() {
    return (
      <MyContext.Provider value={this.state.value}>        <Toolbar />
      </MyContext.Provider>
    );
  }
}
```

#### 5. Ref

##### Кратко

Рефы дают возможность получить доступ к DOM-узлам или React-элементам, созданным (при рендеренге) в рендер-методе.
Чтобы модифицировать потомка (React-компонент или DOM-элемент), необходимо заново отрендерить его с новыми пропсами. 

Ref используется при управлении фокусом, вызове анимаций или интеграции со сторонними библиотеками. Не рекомендуется злоупотреблять ref ами потому что state должен хранится на верхнем уровне иерархии.

Рефы создаются с помощью `React.createRef()` и прикрепляются к React-элементам через `ref` атрибут. Обычно рефы присваиваются свойству экземпляра класса в конструкторе, чтобы на них можно было ссылаться из любой части компонента.

```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.myRef = React.createRef();  }
  render() {
    return <div ref={this.myRef} />;  }
}
```

Когда реф передаётся элементу в методе `render`, ссылка на данный узел доступна через свойство рефа `current`.

```
const node = this.myRef.current;
```

##### Подробно

Рефы дают возможность получить доступ к DOM-узлам или React-элементам, созданным в рендер-методе.

В обычном потоке данных React родительские компоненты могут взаимодействовать с дочерними только через [пропсы](https://ru.reactjs.org/docs/components-and-props.html). Чтобы модифицировать потомка, вы должны заново отрендерить его с новыми пропсами. Тем не менее, могут возникать ситуации, когда вам требуется императивно изменить дочерний элемент, обойдя обычный поток данных. Подлежащий изменениям дочерний элемент может быть как React-компонентом, так и DOM-элементом. React предоставляет лазейку для обоих случаев.

##### Когда использовать рефы

Ситуации, в которых использование рефов является оправданным:

-   Управление фокусом, выделение текста или воспроизведение медиа.
-   Императивный вызов анимаций.
-   Интеграция со сторонними DOM-библиотеками.

Избегайте использования рефов в ситуациях, когда задачу можно решить декларативным способом.

Например, вместо того чтобы определять методы `open()` и `close()` в компоненте `Dialog`, лучше передавать ему проп `isOpen`.

##### Не злоупотребляйте рефами

Возможно, с первого взгляда вам показалось, что рефы применяются, когда нужно решить какую-то задачу в вашем приложении «во что бы то ни стало». Если у вас сложилось такое впечатление, сделайте паузу и обдумайте, где должно храниться конкретное состояние в иерархии компонентов. Часто становится очевидно, что правильным местом для хранения состояния является верхний уровень в иерархии. Подробнее об этом — в главе [Подъём состояния](https://ru.reactjs.org/docs/lifting-state-up.html).

> Примечание
> Приведённые ниже примеры были обновлены с использованием API-метода `React.createRef()` добавленного в React 16.3. Если вы используете более старую версию React, мы рекомендуем использовать [колбэк-рефы](https://ru.reactjs.org/docs/refs-and-the-dom.html#callback-refs).

##### Создание рефов

Рефы создаются с помощью `React.createRef()` и прикрепляются к React-элементам через `ref` атрибут. Обычно рефы присваиваются свойству экземпляра класса в конструкторе, чтобы на них можно было ссылаться из любой части компонента.

```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.myRef = React.createRef();  }
  render() {
    return <div ref={this.myRef} />;  }
}
```

##### Доступ к рефам

Когда реф передаётся элементу в методе `render`, ссылка на данный узел доступна через свойство рефа `current`.

```
const node = this.myRef.current;
```

Значение рефа отличается в зависимости от типа узла:

-   Когда атрибут `ref` используется с HTML-элементом, свойство `current` созданного рефа в конструкторе с помощью `React.createRef()` получает соответствующий DOM-элемент.
-   Когда атрибут `ref` используется с классовым компонентом, свойство `current` объекта-рефа получает экземпляр смонтированного компонента.
-   **Нельзя использовать `ref` атрибут с функциональными компонентами**, потому что для них не создаётся экземпляров.

Представленные ниже примеры демонстрируют отличия в зависимости от типа узла.

###### Добавление рефа к DOM-элементу

В представленном ниже примере `ref` используется для хранения ссылки на DOM-элемент.

```
class CustomTextInput extends React.Component {
  constructor(props) {
    super(props);
    // создадим реф в поле `textInput` для хранения DOM-элемента
    this.textInput = React.createRef();    this.focusTextInput = this.focusTextInput.bind(this);
  }

  focusTextInput() {
    // Установим фокус на текстовое поле с помощью чистого DOM API
    // Примечание: обращаемся к "current", чтобы получить DOM-узел
    this.textInput.current.focus();  }

  render() {
    // описываем, что мы хотим связать реф <input>
    // с `textInput` созданным в конструкторе
    return (
      <div>
        <input
          type="text"
          ref={this.textInput} />        <input
          type="button"
          value="Фокус на текстовом поле"
          onClick={this.focusTextInput}
        />
      </div>
    );
  }
}
```

React присвоит DOM-элемент свойству `current` при монтировании компонента и присвоит обратно значение `null` при размонтировании. Обновление свойства `ref` происходит перед вызовом методов `componentDidMount` и `componentDidUpdate`.

###### Добавление рефа к классовому компоненту

Для того чтобы произвести имитацию клика по `CustomTextInput` из прошлого примера сразу же после монтирования, можно использовать реф, чтобы получить доступ к пользовательскому `<input>` и явно вызвать его метод `focusTextInput`:

```
class AutoFocusTextInput extends React.Component {
  constructor(props) {
    super(props);
    this.textInput = React.createRef();  }

  componentDidMount() {
    this.textInput.current.focusTextInput();  }

  render() {
    return (
      <CustomTextInput ref={this.textInput} />    );
  }
}
```

Обратите внимание, что это сработает только в том случае, если `CustomTextInput` объявлен как классовый компонент:

```
class CustomTextInput extends React.Component {  // ...
}
```

###### Рефы и функциональные компоненты

По умолчанию **нельзя использовать атрибут `ref` с функциональными компонентами**, потому что для них не создаётся экземпляров:

```
function MyFunctionComponent() {  return <input />;
}

class Parent extends React.Component {
  constructor(props) {
    super(props);
    this.textInput = React.createRef();  }
  render() {
    // Данный код *не будет* работать!
    return (
      <MyFunctionComponent ref={this.textInput} />    );
  }
}
```

Если вам нужен реф на функциональный компонент, можете воспользоваться [`forwardRef`](https://ru.reactjs.org/docs/forwarding-refs.html) (возможно вместе с [`useImperativeHandle`](https://ru.reactjs.org/docs/hooks-reference.html#useimperativehandle)), либо превратить его в классовый компонент.

Тем не менее, можно **использовать атрибут `ref` внутри функционального компонента** при условии, что он ссылается на DOM-элемент или классовый компонент:

```
function CustomTextInput(props) {
  // textInput должна быть объявлена здесь, чтобы реф мог иметь к ней доступ  const textInput = useRef(null);
  function handleClick() {
    textInput.current.focus();  }

  return (
    <div>
      <input
        type="text"
        ref={textInput} />      <input
        type="button"
        value="Фокус на поле для ввода текста"
        onClick={handleClick}
      />
    </div>
  );
}
```

##### Передача DOM-рефов родительским компонентам

В редких случаях вам может понадобиться доступ к дочернему DOM-узлу из родительского компонента. В общем случае, такой подход не рекомендуется, т. к. ведёт к нарушению инкапсуляции компонента, но иногда он может пригодиться для задания фокуса или измерения размеров, или положения дочернего DOM-узла.

Несмотря на то, что можно было бы [добавить реф к дочернему компоненту](https://ru.reactjs.org/docs/refs-and-the-dom.html#adding-a-ref-to-a-class-component), такое решение не является идеальным, т. к. вы получите экземпляр компонента вместо DOM-узла. Кроме того, это не сработает с функциональными компонентами.

Если вы работаете с React 16.3 или новее, мы рекомендуем использовать [перенаправление рефов](https://ru.reactjs.org/docs/forwarding-refs.html) для таких случаев. **Перенаправление рефов позволяет компонентам осуществлять передачу рефа любого дочернего компонента как своего собственного**. Вы можете найти детальные примеры того, как передать дочерний DOM-узел родительскому компоненту [в документации по перенаправлению рефов](https://ru.reactjs.org/docs/forwarding-refs.html#forwarding-refs-to-dom-components).

Если вы используете React версии 16.2 или ниже, или если вам нужно решение более гибкое, чем перенаправление рефов, вы можете использовать [данный альтернативный подход](https://gist.github.com/gaearon/1a018a023347fe1c2476073330cc5509) и явно передавать реф как проп с другим именем.

По возможности, мы советуем избегать передачи DOM-узлов, но это может быть полезной лазейкой. Заметим, что данный подход требует добавления кода в дочерний компонент. Если у вас нет никакого контроля над реализацией дочернего компонента, последним вариантом является использование [`findDOMNode()`](https://ru.reactjs.org/docs/react-dom.html#finddomnode), но такое решение не рекомендуется и не поддерживается в [`StrictMode`](https://ru.reactjs.org/docs/strict-mode.html#warning-about-deprecated-finddomnode-usage).

##### Колбэк-рефы

Кроме того, React поддерживает другой способ определения рефов, который называется «колбэк-рефы» и предоставляет более полный контроль над их присвоением и сбросом.

Вместо того, чтобы передавать атрибут `ref` созданный с помощью `createRef()`, вы можете передать функцию. Данная функция получит экземпляр React-компонента или HTML DOM-элемент в качестве аргумента, которые потом могут быть сохранены или доступны в любом другом месте.

Представленный ниже пример реализует общий паттерн: использование колбэка в `ref` для хранения ссылки на DOM-узел в свойстве экземпляра.

```
class CustomTextInput extends React.Component {
  constructor(props) {
    super(props);

    this.textInput = null;
    this.setTextInputRef = element => {      this.textInput = element;    };
    this.focusTextInput = () => {      // Устанавливаем фокус на текстовом поле ввода с помощью чистого DOM API      if (this.textInput) this.textInput.focus();    };  }

  componentDidMount() {
    // устанавливаем фокус на input при монтировании
    this.focusTextInput();  }

  render() {
    // Используем колбэк в `ref`, чтобы сохранить ссылку на DOM-элемент
    // поля текстового ввода в поле экземпляра (например, this.textInput).
    return (
      <div>
        <input
          type="text"
          ref={this.setTextInputRef}        />
        <input
          type="button"
          value="Focus the text input"
          onClick={this.focusTextInput}        />
      </div>
    );
  }
}
```

React вызовет `ref` колбэк с DOM-элементом при монтировании компонента, а также вызовет его со значением `null` при размонтировании. Рефы будут хранить актуальное значение перед вызовом методов `componentDidMount` или `componentDidUpdate`.

Вы можете передавать колбэк-рефы между компонентами точно так же, как и объектные рефы, созданные через `React.createRef()`.

```
function CustomTextInput(props) {
  return (
    <div>
      <input ref={props.inputRef} />    </div>
  );
}

class Parent extends React.Component {
  render() {
    return (
      <CustomTextInput
        inputRef={el => this.inputElement = el}      />
    );
  }
}
```

В представленном выше примере, `Parent` передаёт свой колбэк-реф как проп `inputRef` компоненту `CustomTextInput`, а `CustomTextInput` передаёт ту же самую функцию как специальный атрибут `ref` элементу `<input>`. В итоге свойство `this.inputElement` компонента `Parent` будет хранить значение DOM-узла, соответствующего элементу `<input>` в `CustomTextInput`.

##### Устаревший API: строковые рефы

Если вы уже работали с React ранее, возможно вы знакомы с более старым API, в котором атрибут `ref` является строкой, например`"textInput"`, а DOM-узел доступен в `this.refs.textInput`. Мы не советуем пользоваться таким решением, т. к. у строковых рефов есть [некоторые недостатки](https://github.com/facebook/react/pull/8333#issuecomment-271648615), они являются устаревшими и **будут удалены в одном из будущих релизов**.

> Примечание
> 
> Если вы используете `this.refs.textInput` для доступа к рефам в своих проектах, мы рекомендуем перейти к использованию [паттерна с колбэком](https://ru.reactjs.org/docs/refs-and-the-dom.html#callback-refs) или [`createRef` API](https://ru.reactjs.org/docs/refs-and-the-dom.html#creating-refs).

##### Предостережения насчёт колбэк-рефов

Если `ref` колбэк определён как встроенная функция, колбэк будет вызван дважды во время обновлений: первый раз со значением `null`, а затем снова с DOM-элементом. Это связано с тем, что с каждым рендером создаётся новый экземпляр функции, поэтому React должен очистить старый реф и задать новый. Такого поведения можно избежать, если колбэк в `ref` будет определён с привязанным к классу контекстом, но, заметим, что это не будет играть роли в большинстве случаев.




#### 6. Оптимизация производительности

React использует несколько умных подходов для минимизации количества дорогостоящих DOM-операций, необходимых для обновления пользовательского интерфейса. Для многих приложений, использование React приведёт к быстрому пользовательскому интерфейсу без особых усилий по оптимизации производительности. Тем не менее, существует несколько способов ускорить React-приложение.

##### Использование продакшен-сборки

Если вы испытываете проблемы с производительностью в React-приложении, убедитесь в том, что вы проводите тесты с настройками минифицированной продакшен-сборки.

По умолчанию в React есть много вспомогательных предупреждений, очень полезных при разработке. Тем не менее, они делают React больше и медленнее, поэтому вам обязательно следует использовать продакшен-версию при деплое приложения.

Если вы не уверены в том, что процесс сборки настроен правильно, вы можете проверить это, установив [React Developer Tools for Chrome](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi). Если вы посетите сайт, работающий на React в продакшен-режиме, иконка будет с чёрным фоном:

[![React DevTools on a website with production version of React](https://ru.reactjs.org/static/d0f767f80866431ccdec18f200ca58f1/0a47e/devtools-prod.png)](https://ru.reactjs.org/static/d0f767f80866431ccdec18f200ca58f1/0a47e/devtools-prod.png)

Если вы посетите сайт с React в режиме разработки, у иконки будет красный фон:

[![React DevTools on a website with development version of React](https://ru.reactjs.org/static/e434ce2f7e64f63e597edf03f4465694/0a47e/devtools-dev.png)](https://ru.reactjs.org/static/e434ce2f7e64f63e597edf03f4465694/0a47e/devtools-dev.png)

Как правило, режим разработки используется во время работы над приложением, а продакшен-режим при деплое приложения для пользователей.

Ниже вы можете найти инструкцию по сборке своего приложения для продакшена.

##### Create React App

Если ваш проект сделан с помощью [Create React App](https://github.com/facebookincubator/create-react-app), выполните:

```
npm run build
```

Эта команда создаст продакшен-сборку вашего приложения в папке `build/` вашего проекта.

Помните, что это необходимо только перед деплоем на продакшен. Для обычной разработки используйте `npm start`.

##### Однофайловые сборки

Мы предлагаем готовые для продакшена версии React и React DOM в виде отдельных файлов:

```
<script src="https://unpkg.com/react@18/umd/react.production.min.js"></script>
<script src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js"></script>
```

Помните, что для продакшена подходят только те файлы, которые заканчиваются на `.production.min.js`.

##### Brunch

Для наиболее эффективной продакшен-сборки с Brunch, установите плагин [`terser-brunch`](https://github.com/brunch/terser-brunch).

```
# В случае использования npm
npm install --save-dev terser-brunch

# В случае использования Yarn
yarn add --dev terser-brunch
```

Затем, для создания продакшен сборки, добавьте флаг `-p` к команде `build`:

```
brunch build -p
```

Помните, что это нужно делать только для продакшен-сборки. Вам не нужно использовать флаг `-p` или применять этот плагин во время разработки, потому что это скроет вспомогательные предупреждения React и замедлит процесс сборки.

##### Browserify

Для наиболее эффективной продакшен-сборки с Browserify, установите несколько плагинов:

```
# В случае использования npm
npm install --save-dev envify terser uglifyify

# В случае использования Yarn
yarn add --dev envify terser uglifyify
```

При создании продакшен-сборки, убедитесь, что вы добавили эти пакеты для преобразования **(порядок имеет значение)**:

-   Плагин [`envify`](https://github.com/hughsk/envify) обеспечивает правильную среду для сборки. Сделайте его глобальным (`-g`).
-   Плагин [`uglifyify`](https://github.com/hughsk/uglifyify) удаляет импорты, добавленные при разработке. Сделайте его глобальным (`-g`).
-   Наконец, полученная сборка отправляется к [`terser`](https://github.com/terser-js/terser) для минификации ([прочитайте, зачем это нужно](https://github.com/hughsk/uglifyify#motivationusage)).

К примеру:

```
browserify ./index.js \
  -g [ envify --NODE_ENV production ] \
  -g uglifyify \
  | terser --compress --mangle > ./bundle.js
```

Помните, что это нужно делать только для продакшен-сборки. Вам не следует использовать эти плагины в процессе разработки, потому что это скроет вспомогательные предупреждения React и замедлит процесс сборки.

##### Rollup

Для наиболее эффективной продакшен-сборки с Rollup, установите несколько плагинов:

```
# В случае использования npm
npm install --save-dev rollup-plugin-commonjs rollup-plugin-replace rollup-plugin-terser

# В случае использования Yarn
yarn add --dev rollup-plugin-commonjs rollup-plugin-replace rollup-plugin-terser
```

При создании продакшен-сборки, убедитесь, что вы добавили эти плагины **(порядок имеет значение)**:

-   Плагин [`replace`](https://github.com/rollup/rollup-plugin-replace) обеспечивает правильную среду для сборки.
-   Плагин [`commonjs`](https://github.com/rollup/rollup-plugin-commonjs) обеспечивает поддержку CommonJS в Rollup.
-   Плагин [`terser`](https://github.com/TrySound/rollup-plugin-terser) сжимает и оптимизирует финальную сборку.

```
plugins: [
  // ...
  require('rollup-plugin-replace')({
    'process.env.NODE_ENV': JSON.stringify('production')
  }),
  require('rollup-plugin-commonjs')(),
  require('rollup-plugin-terser')(),
  // ...
]
```

Полный пример настройки можно [посмотреть здесь](https://gist.github.com/Rich-Harris/cb14f4bc0670c47d00d191565be36bf0).

Помните, что это нужно делать только для продакшен-сборки. Вам не следует использовать плагин `terser` или плагин `replace` со значением `'production'` в процессе разработки, потому что это скроет вспомогательные предупреждения React и замедлит процесс сборки.

##### webpack

> **Примечание:**
> 
> Если вы используете Create React App, пожалуйста, следуйте [инструкциям выше](https://ru.reactjs.org/docs/optimizing-performance.html#create-react-app).  
> Этот раздел подойдёт для тех, кто самостоятельно настраивает webpack.

Webpack 4.0 и выше по умолчанию минифицирует код в продакшен-режиме.

```
const TerserPlugin = require('terser-webpack-plugin');

module.exports = {
  mode: 'production',
  optimization: {
    minimizer: [new TerserPlugin({ /* additional options here */ })],
  },
};
```

Вы можете узнать об этом больше в [документации webpack](https://webpack.js.org/guides/production/).

Помните, что это нужно делать только для продакшен-сборки. Вам не стоит использовать `TerserPlugin` в процессе разработки, потому что тогда скроются вспомогательные предупреждения React и замедлится процесс сборки.

##### Анализ производительности компонентов с помощью инструмента разработки «Profiler»

Пакеты `react-dom` версии 16.5+ и `react-native` версии 0.57+ предоставляют расширенные возможности анализа производительности в режиме разработки с помощью инструментов разработчика React Profiler. Обзор профайлера можно найти в посте блога [«Введение в React Profiler»](https://ru.reactjs.org/blog/2018/09/10/introducing-the-react-profiler.html). Пошаговое видео-руководство также [доступно на YouTube](https://www.youtube.com/watch?v=nySib7ipZdk).

Если вы ещё не установили инструменты разработчика React, вы можете найти их здесь:

-   [Chrome Browser Extension](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en)
-   [Firefox Browser Extension](https://addons.mozilla.org/en-GB/firefox/addon/react-devtools/)
-   [Standalone Node Package](https://www.npmjs.com/package/react-devtools)

> Примечание
> 
> Профилирование продакшен-пакета для `react-dom` также доступно как `react-dom/profiling`. Подробнее о том, как использовать этот пакет, читайте на [fb.me/react-profiling](https://fb.me/react-profiling)

> Примечание
> 
> До React 17 мы использовали стандартный [User Timing API](https://developer.mozilla.org/en-US/docs/Web/API/User_Timing_API) для профилирования компонентов с помощью вкладки Performance браузера Chrome. Более подробнее об этом способе можно узнать в [статье Бена Шварца (Ben Schwarz)](https://calibreapp.com/blog/react-performance-profiling-optimization).

##### Виртуализация длинных списков

Если ваше приложение рендерит длинные списки данных (сотни или тысячи строк), мы рекомендуем использовать метод известный как «оконный доступ». Этот метод рендерит только небольшое подмножество строк в данный момент времени и может значительно сократить время, необходимое для повторного рендера компонентов, а также количество создаваемых DOM-узлов.

[react-window](https://react-window.now.sh/) и [react-virtualized](https://bvaughn.github.io/react-virtualized/) — это популярные библиотеки для оконного доступа. Они предоставляют несколько повторно используемых компонентов для отображения списков, сеток и табличных данных. Если вы хотите использовать что-то более специфическое для вашего конкретного случая, то вы можете создать собственный компонент с оконным доступом, как это сделано в [Twitter](https://medium.com/@paularmstrong/twitter-lite-and-high-performance-react-progressive-web-apps-at-scale-d28a00e780a3).

##### Избежание согласования

React создаёт и поддерживает внутреннее представление отображаемого пользовательского интерфейса. Оно также включает React-элементы возвращаемые из ваших компонентов. Это представление позволяет React избегать создания DOM-узлов и не обращаться к текущим без необходимости, поскольку эти операции могут быть медленнее, чем операции с JavaScript-объектами. Иногда его называют «виртуальный DOM», но в React Native это работает точно так же.

Когда изменяются пропсы или состояние компонента, React решает нужно ли обновление DOM, сравнивая возвращённый элемент с ранее отрендеренным. Если они не равны, React обновит DOM.

Несмотря на то, что React обновляет только изменённые DOM-узлы, повторный рендеринг всё же занимает некоторое время. В большинстве случаев это не проблема, но если замедление заметно, то вы можете всё ускорить, переопределив метод жизненного цикла `shouldComponentUpdate`, который вызывается перед началом процесса ререндеринга. Реализация этой функции по умолчанию возвращает `true`, указывая React выполнить обновление:

```
shouldComponentUpdate(nextProps, nextState) {
  return true;
}
```

Если вы знаете ситуации, в которых ваш компонент не нуждается в обновлении, вы можете вернуть `false` из `shouldComponentUpdate`, чтобы пропустить весь процесс рендеринга, включая вызов `render()` и так далее ниже по иерархии.

В большинстве случаев вместо того, чтобы писать `shouldComponentUpdate()` вручную, вы можете наследоваться от [`React.PureComponent`](https://ru.reactjs.org/docs/react-api.html#reactpurecomponent). Это эквивалентно реализации `shouldComponentUpdate()` с поверхностным сравнением текущих и предыдущих пропсов и состояния.

##### shouldComponentUpdate в действии

Вот поддерево компонентов. Для каждого из них `SCU` указывает что возвратил `shouldComponentUpdate`, а `vDOMEq` указывает эквивалентны ли отрендеренные React-элементы. Наконец, цвет круга указывает требуется ли согласовать компонент или нет.

[![Дерево компонентов](https://ru.reactjs.org/static/5ee1bdf4779af06072a17b7a0654f6db/cd039/should-component-update.png)](https://ru.reactjs.org/static/5ee1bdf4779af06072a17b7a0654f6db/cd039/should-component-update.png)

Поскольку `shouldComponentUpdate` возвратил `false` для поддерева с корнем C2, React не пытался отрендерить C2, следовательно не нужно вызывать `shouldComponentUpdate` на C4 и C5.

Для C1 и C3 `shouldComponentUpdate` возвратил `true`, поэтому React пришлось спуститься к листьям и проверить их. Для C6 `shouldComponentUpdate` вернул `true`, и поскольку отображаемые элементы не были эквивалентны, React должен был обновить DOM.

Последний интересный случай — C8. React должен был отрисовать этот компонент, но поскольку возвращаемые им React-элементы были равны ранее предоставленным, ему не нужно обновлять DOM.

Обратите внимание, что React должен был делать изменения только для C6. Для C8 этого удалось избежать сравнением отрендеренных React-элементов, а для поддеревьев C2 и C7 даже не пришлось сравнивать элементы, так как нас выручил `shouldComponentUpdate` и `render` не был вызван.

##### Примеры

Если единственный случай изменения вашего компонента это когда переменная `props.color` или `state.count` изменяются, вы могли бы выполнить проверку в `shouldComponentUpdate` следующим образом:

```
class CounterButton extends React.Component {
  constructor(props) {
    super(props);
    this.state = {count: 1};
  }

  shouldComponentUpdate(nextProps, nextState) {
    if (this.props.color !== nextProps.color) {
      return true;
    }
    if (this.state.count !== nextState.count) {
      return true;
    }
    return false;
  }

  render() {
    return (
      <button
        color={this.props.color}
        onClick={() => this.setState(state => ({count: state.count + 1}))}>
        Счётчик: {this.state.count}
      </button>
    );
  }
}
```

В этом коде `shouldComponentUpdate` — это простая проверка на наличие каких-либо изменений в `props.color` или `state.count`. Если эти значения не изменяются, то компонент не обновляется. Если ваш компонент стал более сложным, вы можете использовать аналогичный паттерн «поверхностного сравнения» между всеми полями `props` и `state`, чтобы определить должен ли обновиться компонент. Этот механизм достаточно распространён, поэтому React предоставляет вспомогательную функцию для работы с ним — просто наследуйтесь от `React.PureComponent`. Поэтому, следующий код — это более простой способ добиться того же самого эффекта:

```
class CounterButton extends React.PureComponent {
  constructor(props) {
    super(props);
    this.state = {count: 1};
  }

  render() {
    return (
      <button
        color={this.props.color}
        onClick={() => this.setState(state => ({count: state.count + 1}))}>
        Счётчик: {this.state.count}
      </button>
    );
  }
}
```

В большинстве случаев вы можете использовать `React.PureComponent` вместо написания собственного `shouldComponentUpdate`. Но он делает только поверхностное сравнение, поэтому его нельзя использовать, если пропсы и состояние могут измениться таким образом, который не сможет быть обнаружен при поверхностном сравнении.

Это может стать проблемой для более сложных структур данных. Например, вы хотите, чтобы компонент `ListOfWords` отображал список слов, разделённых через запятую, с родительским компонентом `WordAdder`, который позволяет кликнуть на кнопку, чтобы добавить слово в список. Этот код работает _неправильно_:

```
class ListOfWords extends React.PureComponent {
  render() {
    return <div>{this.props.words.join(',')}</div>;
  }
}

class WordAdder extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      words: ['словцо']
    };
    this.handleClick = this.handleClick.bind(this);
  }

  handleClick() {
    // Данная секция содержит плохой код и приводит к багам
    const words = this.state.words;
    words.push('словцо');
    this.setState({words: words});
  }

  render() {
    return (
      <div>
        <button onClick={this.handleClick} />
        <ListOfWords words={this.state.words} />
      </div>
    );
  }
}
```

Проблема в том, что `PureComponent` сделает сравнение по ссылке между старыми и новыми значениями `this.props.words`. Поскольку этот код мутирует массив `words` в методе `handleClick` компонента `WordAdder`, старые и новые значения `this.props.words` при сравнении по ссылке будут равны, даже если слова в массиве изменились. `ListOfWords` не будет обновляться, даже если он содержит новые слова, которые должны быть отрендерены.

##### Сила иммутабельных данных

Лучший способ решения этой проблемы — избегать мутирования значений, которые вы используете как свойства или состояние. К примеру, описанный выше метод `handleClick` можно переписать с помощью `concat` следующим образом:

```
handleClick() {
  this.setState(state => ({
    words: state.words.concat(['словцо'])
  }));
}
```

ES6 поддерживает [синтаксис расширения](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Operators/Spread_syntax) для массивов, который поможет сделать это проще. Если вы используете Create React App, то этот синтаксис доступен там по умолчанию.

```
handleClick() {
  this.setState(state => ({
    words: [...state.words, 'словцо'],
  }));
};
```

Таким же образом вы можете переписать код, который мутирует объекты. К примеру, мы имеем объект с именем `colormap` и хотим написать функцию, которая изменяет `colormap.right` на `'blue'`. Мы могли бы написать:

```
function updateColorMap(colormap) {
  colormap.right = 'blue';
}
```

Чтобы написать это без мутирования исходного объекта, мы можем использовать метод [Object.assign](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object/assign):

```
function updateColorMap(colormap) {
  return Object.assign({}, colormap, {right: 'blue'});
}
```

Функция `updateColorMap` теперь возвращает новый объект, вместо того, чтобы мутировать исходный. Метод `Object.assign` входит в ES6 и требует полифила.

[Синтаксис расширения свойств объекта](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Operators/Spread_syntax) упрощает обновление объектов без мутаций:

```
function updateColorMap(colormap) {
  return {...colormap, right: 'blue'};
}
```

Этот синтаксис был добавлен в JavaScript в ES2018.

Если вы используете Create React App, то `Object.assign` и синтаксис расширения объектов доступны вам по умолчанию.

При работе с глубоко вложенными объектами, постоянное их обновление может запутать. Если вы столкнулись с такой проблемой, обратите внимание на [Immer](https://github.com/mweststrate/immer) или [immutability-helper](https://github.com/kolodny/immutability-helper). Эти библиотеки позволяют писать хорошо читаемый код, не теряя преимуществ иммутабельности.
#### 7. Работа с таймерами

Вызываем constructor => props 
Метод взаимодейсвия при нажатии на кнопку
Укажем состояние изменеяемого компонента.

используем setInterval и clearInterval
Написали фукцию таймера
Для создания интервала и  заносим измененное значение в setState

Довольно простой **компонент обратного отсчета** для **React js**. Также можно управлять паузой и сбросом таймера. Пишем на хуках, используя **useState** и **useEffect**.

```
const CountDown = ({ hours = 0, minutes = 0, seconds = 0 }) => {
  const [paused, setPaused] = React.useState(false);
  const [over, setOver] = React.useState(false);
  const [[h, m, s], setTime] = React.useState([hours, minutes, seconds]);

  const tick = () => {
    if (paused || over) return;

    if (h === 0 && m === 0 && s === 0) {
      setOver(true);
    } else if (m === 0 && s === 0) {
      setTime([h - 1, 59, 59]);
    } else if (s == 0) {
      setTime([h, m - 1, 59]);
    } else {
      setTime([h, m, s - 1]);
    }
  };

  const reset = () => {
    setTime([parseInt(hours), parseInt(minutes), parseInt(seconds)]);
    setPaused(false);
    setOver(false);
  };

  React.useEffect(() => {
    const timerID = setInterval(() => tick(), 1000);
    return () => clearInterval(timerID);
  });

  return (
    <div>
      <p>{`${h.toString().padStart(2, '0')}:${m
        .toString()
        .padStart(2, '0')}:${s.toString().padStart(2, '0')}`}</p>
      <div>{over ? "Time's up!" : ''}</div>
      <button onClick={() => setPaused(!paused)}>
        {paused ? 'Resume' : 'Pause'}
      </button>
      <button onClick={() => reset()}>Restart</button>
    </div>
  );
};
```

##### Пример использования:

```
<CountDown hours={1} minutes={45} />
```