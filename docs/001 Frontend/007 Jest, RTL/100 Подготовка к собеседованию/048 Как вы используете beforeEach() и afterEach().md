---
title: Как вы используете beforeEach() и afterEach() ?
draft: false
tags:
  - testing
  - Jest
  - beforeEach
  - afterEach
---
`beforeEach` и `afterEach` используются для выполнения определенных блоков кода перед и после каждого теста внутри блока `describe`. Они полезны для настройки и очистки тестов.

Пример использования `beforeEach` и `afterEach`:

```javascript
describe('City database tests', () => {
  beforeEach(() => {
    initializeCityDatabase(); // Выполняется перед каждым тестом
  });

  afterEach(() => {
    clearCityDatabase(); // Выполняется после каждого теста
  });

  it('city database has Vienna', () => {
    expect(isCity('Vienna')).toBeTruthy();
  });

  it('city database has San Juan', () => {
    expect(isCity('San Juan')).toBeTruthy();
  });
});
```

В этом примере:
- `initializeCityDatabase()` выполняется перед каждым тестом, чтобы гарантировать, что база данных городов инициализирована.
- `clearCityDatabase()` выполняется после каждого теста, чтобы очистить базу данных и подготовить её к следующему тесту.

____

[[007 Jest, RTL|Назад]]