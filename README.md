<<<<<<< HEAD
# Завдання 1
Клас Student, який містить три властивості: name, age та grade. Замість того, щоб оголошувати ці властивості в тілі класу, потім у конструкторі, і нарешті надавати їм значення, напишіть скорочену ініціалізацію.
```ts
class Student {
  public name: string;
  public age: number;
  public grade: string;

  constructor(name: string, age: number, grade: string) {
    this.name = name;
    this.age = age;
    this.grade = grade;
  }
}
```
# Завдання 2
Ваше завдання полягатиме у створенні двох класів – Employee та Manager.

Клас Employee повинен включати:

властивість name, яка буде доступна всім.
властивість department, яка буде доступна лише всередині класу Employee.
salary, яке буде доступне лише всередині класу Employee та його підкласів.


Клас Manager повинен бути підклас класу Employee

Необхідно реалізувати в класі Manager конструктор, який викликатиме конструктор суперкласу та збільшуватиме salary на 10000.
```ts
class Employee {
  // Заповніть модифікатори доступу
  name: string;
  department: string;
  salary: number;

  constructor(name: string, department: string, salary: number) {
    this.name = name;
    this.department = department;
    this.salary = salary;
  }

  getEmployeeDetails() {
    return `Name: ${this.name}, Department: ${this.department}, Salary: ${this.salary}`;
  }
}

class Manager extends Employee {
  // Реалізуйте конструктор та збільшіть salary на 10000
}
```
# Завдання 3
Ви створюєте гру, де є персонажі з різними ролями. Зараз ви працюєте над класом Wizard, який має реалізовувати два інтерфейси - ICharacter та ISpellCaster.

Визначте інтерфейси ICharacter та ISpellCaster так, щоб вони відповідали вимогам класу Wizard. Інтерфейс ICharacter повинен включати властивості name і level, і навіть метод introduce і levelUp. Інтерфейс ISpellCaster повинен включати метод castSpell.
```ts
// реалізація класу Wizard
class Wizard implements ICharacter, ISpellCaster {
  constructor(public name: string, public level: number) {
    if (this.level < 1) {
      throw new Error('Level too low');
    }
  }

  introduce(phrase: string): void {
    console.log(phrase + ', ' + this.name);
  }

  castSpell(): void {
    console.log('Casting a spell, behold my power!');
  }

  levelUp(): void {
    this.level++;
    console.log(`Level up! New level is ${this.level}`);
  }
}

// тестування класу
const wizard = new Wizard('Merlin', 15);

wizard.introduce('I am the mighty wizard');
wizard.castSpell();
wizard.levelUp();  // Level up! New level is 16
```
# Завдання 4 *
У цьому завдання вам належить реалізувати сценарій життя, де людина, ключ і будинок взаємодіють один з одним.

Ключ (Key): Створіть клас Key. У нього має бути одна приватна властивість signature, яка генерується випадково при створенні об'єкта цього класу (наприклад Math.random()). Також цей клас повинен мати метод getSignature, який повертає значення властивості signature.

Людина (Person): Створіть клас Person. Конструктор цього класу приймає об'єкт класу Key і зберігає їх у приватному властивості key. Клас Person повинен мати метод getKey, який повертає збережений ключ.

Дім (House): Створіть абстрактний клас House. Цей клас має дві властивості: door, яка може бути відкрита (true), або закрита (false), і key, яка зберігає об'єкт класу Key. У цьому класі також повинен бути метод comeIn, який додає об'єкт класу Person у масив tenants, якщо door відкрита. Ваш абстрактний клас House також повинен мати абстрактний метод OpenDoor, який приймає об'єкт класу Key.

Мій будинок (MyHouse): Створіть клас MyHouse, який успадковується від абстрактного класу House. Реалізуйте метод openDoor у цьому класі. Якщо ключ, переданий цьому методу, збігається з ключем, збереженим як key, то двері відчиняються.

Після реалізації всіх класів створіть об'єкти для кожного класу та спробуйте відтворити сценарій, в якому людина приходить додому.

Наприклад, ось так:

```ts
const key = new Key();

const house = new MyHouse(key);
const person = new Person(key);

house.openDoor(person.getKey());

house.comeIn(person);
```
=======
# Базові типи

Метою цього домашнього завдання є закріплення ваших навичок роботи з базовими типами TypeScript. Ви будете працювати з типами, такими як number, string, boolean, null, undefined, unknown, any, а також кортежами, переліками (enum) та об'єднаннями типів.

В кінці домашнього завдання ви також попрактикуєтеся у створенні свого типу на основі наявних об'єктів. Це допоможе вам краще зрозуміти, як TypeScript може бути використаний для забезпечення типової безпеки ваших даних та підвищення якості вашого коду.


### Завдання 1
Є наступний JavaScript код:

```ts
let age = 50;
let name = 'Max';
let toggle = true;
let empty = null;
let notInitialize;
let callback = (a) => { return 100 + a };
```

Перетворіть цей код на TypeScript, вказавши відповідні типи для всіх змінних.

### Завдання 2
JavaScript змінна може зберігати значення будь-якого типу:
```ts
let anything = -20;
anything = 'Text';
anything = {};
```
Який тип ви надаєте змінній anything в TypeScript, щоб зберегти її гнучкість?

### Завдання 3
У TypeScript тип unknown дозволяє нам зберігати будь-які значення, але ми можемо привласнити unknown змінну безпосередньо інший змінної, якщо ми впевнені у її типі. У вас є наступний код:
```ts
let some:unknown;
some = 'Text';
let str: string;
str = some;
```
Що потрібно виправити в цьому коді, щоб він став правильним та безпечним?

### Завдання 4
У вас є наступний JavaScript масив:
```ts
let person = ['Max', 21];
```
Як переписати його в TypeScript, використовуючи концепцію кортежів, щоб гарантувати, що перший елемент завжди буде рядком, а другий числом?

### Завдання 5
Як ви визначите змінну в TypeScript, яка може приймати рядок або число (union type)? І так само визначте змінну, яка може приймати тільки одне з двох рядкових значень: 'enable' або 'disable' (literal type)?

### Завдання 6
У вас є такі функції JavaScript:
```ts
function showMessage(message) {
  console.log(message);
}

function calc(num1, num2) {
  return num1 + num2;
}

function customError() {
  throw new Error('Error');
}
```
Як ви вкажете типи для аргументів і значень цих функцій, що повертаються?

### Завдання 7
Створіть функцію (isWeekend), яка приймає день тижня (з вашого enum) і повертає boolean значення, що вказує, чи це день робочий чи вихідний.

### Завдання 8
Створіть тип "Gender", використовуючи union type, який може містити значення "male", "female". Створіть змінну myGender цього типу.

### Завдання 9
У вас є два об'єкти:
```ts
const page1 = {
  title: 'The awesome page',
  likes: 100,
  accounts: ['Max', 'Anton', 'Nikita'],
  status: 'open',
  details: {
    createAt: new Date('2021-01-01'),
    updateAt: new Date('2021-05-01'),
  }
}

const page2 = {
  title: 'Python or Js',
  likes: 5,
  accounts: ['Alex'],
  status: 'close',
}
```
Створіть новий тип даних, який підходить для цих двох об'єктів.

# Generic
Мета цього завдання - допомогти вам зрозуміти та застосувати generics у TypeScript. Ви працюватимете з функціями, що повертають проміси, використовувати вбудований тип Pick, об'єднувати об'єкти за допомогою generics, а також вирішувати проблеми типів у класах.

### Завдання 1
Є функція getPromise(), яка повертає проміс, що дозволяється в масив, що містить рядки та числа. Доповніть цю функцію, використовуючи generics, щоб вона повертала правильний тип.
```ts
function getPromise () {
  return new Promise((resolve) => {
    resolve(['Text', 50]);
  });
}

getPromise()
.then((data) => {
  console.log(data);
});
```
### Завдання 2
У вас є тип AllType. Існує функція compare, яка приймає два об'єкти. Ці об'єкти містять поля AllType. Ваше завдання – використовувати Pick та generics для вказівки, що поля цих об'єктів належать AllType. Функція compare повинна повертати AllType.
```ts
type AllType = {
  name: string;
  position: number;
  color: string;
  weight: number
}

function compare (top, bottom): AllType {
  return {
    name: top.name,
    color: top.color,
    position: bottom.position,
    weight: bottom.weight,
  }
}
```
### Завдання 3
У вас є функція merge, яка поєднує два об'єкти. Використовуйте generics, щоб вказати, що ці об'єкти можуть бути будь-якого типу.
```ts
function merge (objA, objB) {
  return Object.assign(objA, objB);
}
```
### Завдання 4
Використовуйте generics та інтерфейси, щоб виправити помилку в наступних класах:
```ts
class Component {
  constructor (public props:T) {

  }
}

class Page extends Component {
  pageInfo () {
    console.log(this.props.title);
  }
}
```
### Завдання 5
Вам потрібно реалізувати інтерфейс KeyValuePair, який описує пару ключ-значення. Використовуйте generics, щоб цей інтерфейс міг працювати з будь-якими типами ключів та значень.
```ts
interface KeyValuePair {
  key;
  value;
}
```
### Завдання 6
Ви маєте форму реєстрації користувачів. Іноді потрібно попередньо заповнити форму даними користувача для оновлення його профілю. Однак вам не завжди потрібно заповнити всі поля. Наприклад, користувач може хотіти оновити лише свій email та пароль, залишивши ім'я та прізвище без змін.

Виправте тип у аргументі функції так, щоб не було помилок типу.
```ts
type User = {
  name: string;
  surname: string;
  email: string;
  password: string;
}

function createOrUpdateUser(initialValues: User) {
  // Оновлення користувача
}

createOrUpdateUser({ email: 'user@mail.com', password: 'password123' });
```
### Завдання 7
У вас є перелік UserRole, який використовується для класифікації користувачів у вашому додатку. Ви хочете створити об'єкт RoleDescription, який зіставлятиме кожну роль користувача з її описом.
```ts
export enum UserRole {
  admin = 'admin',
  editor = 'editor',
  guest = 'guest',
}

// Замініть наступний код на версію за допомогою Record
const RoleDescription = {
  admin: 'Admin User',
  editor: 'Editor User',
  guest: 'Guest User',
};
```
### Завдання 8
У вас є тип Form, який містить інформацію про форму, включаючи поле errors. Ви хочете створити новий тип Params, який включає всі поля з Form, крім errors.
```ts
type Errors = {
  email?: string[];
  firstName?: string[];
  lastName?: string[];
  phone?: string[];
};

type Form = {
  email: string | null;
  firstName: string | null;
  lastName: string | null;
  phone: string | null;
  errors: Errors;
};

// Реалізуйте Params так, щоб унеможливити поле 'errors' з типу Form
type Params = Form;
``
>>>>>>> 888b3cfa00d9d8551f38cb046d3f51c7a5306152
