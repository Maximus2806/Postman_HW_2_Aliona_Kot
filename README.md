### `http://162.55.220.72:5005/first`
1. Отправить запрос.
2. Статус код 200
```
pm.test("Status code is 200", function () {
  pm.response.to.have.status(200);
});
```
3. Проверить, что в body приходит правильный string.
```
pm.test("Body matches string", function () {
  pm.expect(pm.response.text()).to.include("This is the first responce from server!");
});
```
### `http://162.55.220.72:5005/user_info_3`
1. Отправить запрос.
2. Статус код 200
```
pm.test("Status code is 200", function () {
  pm.response.to.have.status(200);
});
```
3. Спарсить response body в json.
```
let jsonData = pm.response.json ()
```
4. Проверить, что name в ответе равно name s request (name вбить руками.)
```
pm.test("Name = Alona", function () {
    pm.expect(jsonData.name).to.eql("Alona");
});
```
5. Проверить, что age в ответе равно age s request (age вбить руками.)
```
pm.test("Age = 25", function () {
    pm.expect(jsonData.age).to.eql("25");
});
```
6. Проверить, что salary в ответе равно salary s request (salary вбить руками.)
```
pm.test("Salary = 1000", function () {
    pm.expect(jsonData.salary).to.eql(1000);
});
```
7. Спарсить request.
```
let reqData = request.data
```
8. Проверить, что name в ответе равно name s request (name забрать из request.)
```
pm.test("Name = BodyName", function () {
    pm.expect(jsonData.name).to.eql(reqData.name);
});
```
9. Проверить, что age в ответе равно age s request (age забрать из request.)
```
pm.test("Age = BodyAge", function () {
    pm.expect(jsonData.age).to.eql(reqData.age);
});
```
10. Проверить, что salary в ответе равно salary s request (salary забрать из request.)
```
let salaryInt = parseInt(reqData.salary)

pm.test("Salary = BodySalary", function () {
    pm.expect(jsonData.salary).to.eql(salaryInt);
});

```
11. Вывести в консоль параметр family из response.
```
console.log(jsonData.family);
```
12. Проверить что u_salary_1_5_year в ответе равно salary*4 (salary забрать из request)
```
pm.test("u_salary_1_5_year", function () {
    pm.expect(jsonData.family.u_salary_1_5_year).to.eql(salaryInt*4);
});
```

### `http://162.55.220.72:5005/object_info_3`
1. Отправить запрос.
2. Статус код 200
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
3. Спарсить response body в json.
```
let jsonData = pm.response.json ()
```
4. Спарсить request.
```
let reqData = pm.request.url.query.toObject ();
let salaryInt = parseInt(reqData.salary)
```
5. Проверить, что name в ответе равно name s request (name забрать из request.)
```
pm.test("Name = ParamsName", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.name).to.eql(reqData.name);
});
```
6. Проверить, что age в ответе равно age s request (age забрать из request.)
```
pm.test("Age = ParamsAge", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.age).to.eql(reqData.age);
});
```
7. Проверить, что salary в ответе равно salary s request (salary забрать из request.)
```
pm.test("Salary = ParamsSalary", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.salary).to.eql(salaryInt);
});
```
8. Вывести в консоль параметр family из response.
```
console.log(respData.family);
```
9. Проверить, что у параметра dog есть параметры name.
```
pm.test("Dog has a name", function () {
    var respData = pm.response.json();
    pm.expect(respData.family.pets.dog).to.have.property("name");
});
```
10. Проверить, что у параметра dog есть параметры age.
```
pm.test("Dog has an age", function () {
    var respData = pm.response.json();
    pm.expect(respData.family.pets.dog).to.have.property("age");
});
```
11. Проверить, что параметр name имеет значение Luky.
```
pm.test("Dog has name Luky", function () {
    var respData = pm.response.json();
    pm.expect(respData.family.pets.dog.name).to.eql("Luky");
});
```
12. Проверить, что параметр age имеет значение 4.
```
pm.test("Dog has age 4", function () {
    var respData = pm.response.json();
    pm.expect(respData.family.pets.dog.age).to.eql(4);
});
```

### `http://162.55.220.72:5005/object_info_4`
1. Отправить запрос.
2. Статус код 200
3. Спарсить response body в json.
4. Спарсить request.
5. Проверить, что name в ответе равно name s request (name забрать из request.)
6. Проверить, что age в ответе равно age из request (age забрать из request.)
7. Вывести в консоль параметр salary из request.
8. Вывести в консоль параметр salary из response.
9. Вывести в консоль 0-й элемент параметра salary из response.
10. Вывести в консоль 1-й элемент параметра salary параметр salary из response.
11. Вывести в консоль 2-й элемент параметра salary параметр salary из response.
12. Проверить, что 0-й элемент параметра salary равен salary из request (salary забрать из request.)
13. Проверить, что 1-й элемент параметра salary равен salary*2 из request (salary забрать из request.)
14. Проверить, что 2-й элемент параметра salary равен salary*3 из request (salary забрать из request.)
15. Создать в окружении переменную name
16. Создать в окружении переменную age
17. Создать в окружении переменную salary
18. Передать в окружение переменную name
19. Передать в окружение переменную age
20. Передать в окружение переменную salary
21. Написать цикл который выведет в консоль по порядку элементы списка из параметра salary.
