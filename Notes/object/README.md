# Object

```jsx
let person = {
    firstName: 'Serkan',
    lastName: 'ISIK',
    yearOfBirth: 1998,
    married: false,
    favoriteColors: ['Black', 'White', "Grey"],
		//Method: Object içindeki fonksiyon
    calculateAge: function () { 
        this.age = 2022 - this.yearOfBirth;
    }
};

console.log(person.firstName);
console.log(person.lastName);
console.log(person.yearOfBirth);
console.log(person.married);
console.log(person.favoriteColors);

person.calculateAge(); 
console.log(person.age); //you have to call the function first
```

![Untitled](Untitled.png)

```jsx
let person = {
    firstName: 'Serkan',
    lastName: 'ISIK',
    yearOfBirth: 1998,
    married: false,
    favoriteColors: ['Black', 'White', "Grey"],
};

console.log(person['firstName']);
console.log(person['lastName']);
console.log(person['yearOfBirth']);
console.log(person['married']);
console.log(person['favoriteColors']);
```

![Untitled](Untitled%201.png)

```jsx
let person = {
    firstName: 'Serkan',
    lastName: 'ISIK',
    yearOfBirth: 1998,
    married: false,
    favoriteColors: ['Black', 'White', "Grey"],
};

let person2 = {
    firstName: 'Esmanur',
    lastName: 'MAZLUM',
    yearOfBirth: 2000,
    married: false,
    favoriteColors: ['Black', 'Green', "Blue"],
};

//Array
let people = [person, person2];

console.log(people);
console.log(people[0].firstName);
console.log(people[1].firstName);
```

![Untitled](Untitled%202.png)

```jsx
let person = new Object();

person.firstName = "Serkan";
person.lastName = "ISIK"
person.yearOfBirth = 1998;

console.log(person.firstName);
console.log(person.lastName);
console.log(person.yearOfBirth);
```

![Untitled](Untitled%203.png)

---

## Second Part

```jsx
let person = {
    firstName: 'Serkan',
    lastName: 'ISIK',
    //year-Of-Birth: 1998,  //Hatalı !
    ['year-Of-Birth']: 1998 // "-"  kullanımı
};

console.log(person.firstName);
console.log(person.lastName);
console.log(person['year-Of-Birth']);
```

![Untitled](Untitled%204.png)

```jsx
//object literals
let person = {
    firstName: 'Serkan',
    age: 23,
    bilgileriSoyle: function () {
        return `Benim adım ${this.firstName} ben ${this.age} yaşındayım`; //template literal				
    }
};

console.log(person.bilgileriSoyle());
```

![Untitled](Untitled%205.png)

```jsx
let person = {
    firstName: 'Serkan',
    age: 23
};

console.log(person);

person.age = 24;

console.log(person);

person.lastName = 'ISIK';

console.log(person);

//Oluşturulan yapıyı sonradan değiştirmek önerilmez, çünkü takibi zorlaşır.
```

![Untitled](Untitled%206.png)

### Factory Functions

```jsx
let person = {
    firstName: 'Serkan',
    lastName: 'ISIK',
    age: 23,
};
console.log(person);

console.log("--------------");

//factory functions
//bu fonksiyon object döndürür.
function createPerson(parFirstName,parLastName,parAge){
    return {
        firstName: parFirstName,
        lastName: parLastName,
        age: parAge
    }
}

const serkan = createPerson('Serkan', 'ISIK', 23);
console.log(serkan);

const esmanur = createPerson('Esmanur', 'MAZLUM', 21);
console.log(esmanur);
```

![Untitled](Untitled%207.png)

![Untitled](Untitled%208.png)

```jsx
function createPerson(parFirstName,parLastName,parAge){
    return {
        firstName: parFirstName,
        lastName: parLastName,
        age: parAge,
        bilgileriGoster: function (){
            return `Benim adım ${this.firstName} ben ${this.age} yaşındayım`;
        }
    }
}

const serkan = createPerson('Serkan', 'ISIK', 23);
console.log(serkan.bilgileriGoster());

const esmanur = createPerson('Esmanur', 'MAZLUM', 21);
console.log(esmanur.bilgileriGoster());
```

![Untitled](Untitled%209.png)

# Constructor Functions

```jsx
//constructor functions
function Ogrenci (parFirstName,parLastName,parAge){
    this.firstName = parFirstName;
    this.lastName = parLastName;
    this.age = parAge;
    this.bilgileriGoster = function () {
        return `Benim adım ${this.firstName} ben ${this.age} yaşındayım`;
    }
}

const serkan = new Ogrenci('Serkan','ISIK',23); //instance

console.log(serkan);
console.log(serkan.bilgileriGoster());

/*
new kullanıldığında:
1- Yeni bir object oluşturulur.
2- factory functions 'lardaki gibi return kullanılmak zorunda kalınmaz
3- this kelimesini o an oluşturulacak olan object'e bağlar
*/
```

![Untitled](Untitled%2010.png)

---

```jsx
function Ogrenci (parFirstName,parLastName,parAge){
    this.firstName = parFirstName;
    this.lastName = parLastName;
    this.age = parAge;
    this.bilgileriGoster = function () {
        return `Benim adım ${this.firstName} ben ${this.age} yaşındayım`;
    }
    console.log(this); // Dikkat !
}

const serkan = new Ogrenci('Serkan','ISIK',23);
```

![Untitled](Untitled%2011.png)

---

<aside>

📌 Her Object ’in bir constructor ‘ı vardır.

</aside>

<aside>

📌 Javascript 'deki tüm objeler onu oluşturan constructor fonksiyonun tanımına
erişebilir.

</aside>

```
function Ogrenci (parFirstName,parLastName,parAge){
    this.firstName = parFirstName;
    this.lastName = parLastName;
    this.age = parAge;
    this.bilgileriGoster = function () {
        return `Benim adım ${this.firstName} ben ${this.age} yaşındayım`;
    }
}

const serkan = new Ogrenci('Serkan','ISIK',23);

console.log(serkan.constructor);
```

![Untitled](Untitled%2012.png)

<aside>

📌 Array ve Fuction ‘lar da birer object ’dir. Onlar da kurucu constructor ‘larına erişebilirler.

</aside>

```jsx
const myObject = {};
console.log(myObject.constructor);

const myArray = [];
console.log(myArray.constructor);

const myFunction = function () {
};
console.log(myFunction.constructor);

/* Javascript temelinde kendilerini oluşturan kurucu fonksiyona eriştik fakat
kod içeriği bizimle paylaşılmıyor*/ 
```

![Untitled](Untitled%2013.png)

---

```jsx
const myObject = {};
console.log(myObject); //myObject'in constructor'ına eriştik

const myArray = [];
console.log(myArray); 

const myFunction = function () {
};
console.log(myFunction);
```

![Untitled](Untitled%2014.png)

---

```jsx
const myObject = {};
console.log(myObject.constructor()); // boş bir object oluşturuldu

const myArray = [];
console.log(myArray.constructor()); // boş bir array oluşturuldu

const myFunction = function () {
};
console.log(myFunction.constructor()); // boş bir fonksiyon oluşturuldu

```

![Untitled](Untitled%2015.png)

```jsx
function Ogrenci (parFirstName,parLastName,parAge){
    this.firstName = parFirstName;
    this.lastName = parLastName;
    this.age = parAge;
    this.bilgileriGoster = function () {
        return `Benim adım ${this.firstName} ben ${this.age} yaşındayım`;
    }
}

const serkan = new Ogrenci('Serkan','ISIK',23);

console.log(serkan);

const esmanur = new serkan.constructor('Esmanur', 'MAZLUM', 21);

console.log(esmanur);

/*serkan object'inin kurucu fonksiyonunu Ogrenci 'ye erişip yeni bir 
object oluşturduk.*/
```

![Untitled](Untitled%2016.png)

```jsx
const myObject = {};
const secondObject = myObject.constructor(); // boş bir object oluşturuldu

console.log(myObject);
console.log(secondObject);

console.log("----------");

const myArray = [];
const secondArray = myArray.constructor(); // boş bir array oluşturuldu

console.log(myArray);
console.log(secondArray);

console.log("----------");

const myFunction = function () {
};
const secondFunction = myFunction.constructor(); // boş bir fonksiyon oluşturuldu

console.log(myFunction);
console.log(secondFunction);
```

---

# Prototype Property

<aside>

📌 JS prototyoe miras modelini kullanır.

</aside>

<aside>

📌 Her constructor function/class ayrı kurucu fonksiyonlar oluşturulan instance’ların ortak olarak kullanabilecekleri prototype isimli property ‘e sahiptir.

</aside>

<aside>

📌 Prototype property de bir nesne döndürür.

</aside>

```jsx
//constructor functions
function Family (parFirstName,parLastName,parAge){
    this.firstName = parFirstName;
    this.lastName = parLastName;
    this.age = parAge;
    this.bilgileriGoster = function () {
        return `Benim adım ${this.firstName} soyadım ${this.lastName} ve ${this.age} yaşındayım`;
    }
}

const durdu = new Family('Durdu','ISIK',56); //instance

const emine = new Family('Emine','ISIK',54); //instance

const hakan = new Family('Hakan','ISIK',33); //instance

const nurcan = new Family('Nurcan','ISIK',28); //instance

const aysegul = new Family('Aysegul','ISIK',26); //instance

const serkan = new Family('Serkan','ISIK',23); //instance

console.log(durdu);
console.log(durdu.bilgileriGoster());

console.log(emine);
console.log(emine.bilgileriGoster());

console.log(hakan);
console.log(hakan.bilgileriGoster());

console.log(nurcan);
console.log(nurcan.bilgileriGoster());

console.log(serkan);
console.log(serkan.bilgileriGoster());
```

![Untitled](Untitled%2017.png)

---

```jsx
Family.prototype.lastName = 'ISIK';
Family.prototype.bilgileriGoster = function () {
    return `Benim adım ${this.firstName} soyadım ${this.lastName} ve ${this.age} yaşındayım`;
}

//constructor functions
function Family (parFirstName,parAge){
    this.firstName = parFirstName;
    this.age = parAge;
}

const durdu = new Family('Durdu',56); //instance

const emine = new Family('Emine',54); //instance

const hakan = new Family('Hakan',33); //instance

const nurcan = new Family('Nurcan',28); //instance

const aysegul = new Family('Aysegul',26); //instance

const serkan = new Family('Serkan',23); //instance

console.log(durdu);
console.log(durdu.bilgileriGoster());

console.log(emine);
console.log(emine.bilgileriGoster());

console.log(hakan);
console.log(hakan.bilgileriGoster());

console.log(nurcan);
console.log(nurcan.bilgileriGoster());

console.log(serkan);
console.log(serkan.bilgileriGoster());
```

![Untitled](Untitled%2018.png)

<aside>

💡 Prototype property sayesinde her instance için ayrı ayrı ‘ISIK’ argümanı yazılmak zorunda kalınmadı.

</aside>

---

```jsx
Family.prototype.lastName = 'ISIK';
Family.prototype.bilgileriGoster = function () {
    return `Benim adım ${this.firstName} soyadım ${this.lastName} ve ${this.age} yaşındayım`;
}

//constructor functions
function Family (parFirstName,parAge){
    this.firstName = parFirstName;
    this.age = parAge;
}

const durdu = new Family('Durdu',56); //instance

console.log(durdu.constructor);

console.log(durdu.constructor.prototype);
//Prototype property de bir nesne döndürür.

console.log(Object.getPrototypeOf(durdu));
```

![Untitled](Untitled%2019.png)

```jsx
const myArray = [1, 2, 3];
console.log(myArray);

myArray.push(4);
console.log(myArray);

/* 
Oluşturulan tüm Array 'ler Array sınıfına ait prototipleri
kullanabilir. 
Bunlara örnek olarak push() fonksiyonu verilebilir.

Tamımladığımız bütün arrayler Array sınıfının 
prototipi kullanılarak oluşturulur. Bu sayede Array sınıfına
ait olan bütün fonksiyonları kullanabilirler.
*/

/*
push() fonksiyonu prototipe olarak tanımlanmıştır
ve oluşan her arrayin bu fonksiyonu kullanabilmesi sağlanmıştır
*/

console.log(myArray.constructor);
console.log(myArray.constructor.prototype);

/* Javascript oluşturanlar bu fonksiyonları prototype olarak
tanımlanmıştır. 
Bu sayede myArray. yazarak fonksiyonları kullanabiliyoruz */
```

![Untitled](Untitled%2020.png)

```jsx
/*Aslında olay bunlardan fazlası...

Array'ler de function 'lar da birer objedir...

Demek ki Object diye bir yapı var...
Ve Array 'ler Function 'lar ve Object 'ler onun da değerlerini
kullanabiliyor. 
*/
const myArray = [1, 2, 3];

console.log(myArray.constructor.prototype);
```

![Untitled](Untitled%2021.png)

![Untitled](Untitled%2022.png)

---

# toString İncelemesi

![Untitled](Untitled%2021.png)

```jsx
Family.prototype.lastName = 'ISIK';
Family.prototype.bilgileriGoster = function () {
    return `Benim adım ${this.firstName} soyadım ${this.lastName} ve ${this.age} yaşındayım`;
}

//constructor functions
function Family (parFirstName,parAge){
    this.firstName = parFirstName;
    this.age = parAge;
}

const durdu = new Family('Durdu',56); //instance

console.log(durdu.toString());
```

![Untitled](Untitled%2023.png)

```jsx
Family.prototype.lastName = 'ISIK';
Family.prototype.bilgileriGoster = function () {
    return `Benim adım ${this.firstName} soyadım ${this.lastName} ve ${this.age} yaşındayım`;
}

//constructor functions
function Family (parFirstName,parAge){
    this.firstName = parFirstName;
    this.age = parAge;
}

const durdu = new Family('Durdu',56); //instance

console.log("Bir başka örnek: " + durdu);
//durdu otomatik olarak string haline getirilecek
//bunu da kendi tanımladığımız toString yapacak
```

![Untitled](Untitled%2024.png)

### Object ‘e ait olan toString ‘in yeniden tanımlanarak ezilmesi

```jsx
Family.prototype.lastName = 'ISIK';
Family.prototype.bilgileriGoster = function () {
    return `Benim adım ${this.firstName} soyadım ${this.lastName} ve ${this.age} yaşındayım`;
}

Family.prototype.toString = function (){
    return "toString yeniden tanımlandı !";
}

//constructor functions
function Family (parFirstName,parAge){
    this.firstName = parFirstName;
    this.age = parAge;
}

const durdu = new Family('Durdu',56); //instance

console.log(durdu.toString());
```

![Untitled](Untitled%2025.png)

```jsx
Family.prototype.lastName = 'ISIK';
Family.prototype.bilgileriGoster = function () {
    return `Benim adım ${this.firstName} soyadım ${this.lastName} ve ${this.age} yaşındayım`;
}

Family.prototype.toString = function (){
    return "toString yeniden tanımlandı !";
}

//constructor functions
function Family (parFirstName,parAge){
    this.firstName = parFirstName;
    this.age = parAge;
}

const durdu = new Family('Durdu',56); //instance

console.log("Bir başka örnek: " + durdu);
//durdu otomatik olarak string haline getirilecek
//bunu da kendi tanımladığımız toString yapacak
```

![Untitled](Untitled%2026.png)

---

### Object ‘e ait olan toString kullanımı

```jsx
Family.prototype.lastName = 'ISIK';
Family.prototype.bilgileriGoster = function () {
    return `Benim adım ${this.firstName} soyadım ${this.lastName} ve ${this.age} yaşındayım`;
}

//constructor functions
function Family (parFirstName,parAge){
    this.firstName = parFirstName;
    this.age = parAge;
}

const durdu = new Family('Durdu',56); //instance

console.log(durdu.age.toString());
```

![Untitled](Untitled%2027.png)

---

<aside>

❓ toString yeniden tanımlansa da durdu.age.toString(); için toString ‘in default sonucu geldi…

</aside>

```jsx
Family.prototype.lastName = 'ISIK';
Family.prototype.bilgileriGoster = function () {
    return `Benim adım ${this.firstName} soyadım ${this.lastName} ve ${this.age} yaşındayım`;
}

Family.prototype.toString = function (){
    return "toString yeniden tanımlandı !";
}

//constructor functions
function Family (parFirstName,parAge){
    this.firstName = parFirstName;
    this.age = parAge;
}

const durdu = new Family('Durdu',56); //instance

console.log(durdu.toString());
console.log(durdu.age.toString());
```

![Untitled](Untitled%2028.png)

---

# Wrapper Objects (Sarmalayıcı Objeler)

```jsx
const firstName = "Serkan";
console.log(typeof firstName);
console.log(firstName instanceof Object);

console.log("----------");

console.log(firstName.toUpperCase());
console.log(typeof firstName);
console.log(firstName instanceof Object);

/* toUpperCase() Object 'lere özgü bir yapı olmasına
ragmen primitive bir yapı olan firstName toUpperCase() 'i 
nasıl kullandı ? */

console.log("----------");

console.log(firstName.constructor);
//Her bir Object 'in constructor 'ı vardır.
/* firstName primitive bir yapı ise nasıl constructor'u var ? */

console.log("----------");

console.log(firstName.constructor.prototype);
/* firstName primitive bir yapı ise Object'lere ait şeylere nasıl sahip oluyor ?*/

/*
Açıklama:
Javascript primitive bir değişken oluşturulduğunda onları kapsayıcı bir 
değişken içine alır.

Yani firstName toUpperCase() gibi değişkenleri kullanabilsin diye
Javascript firstName değişkenini String isimle Object'in içine alıyor.

firstName Object gibi davranmış oluyor fakat hala string halde kalıyor.
*/

console.log("***********");

//bir string 'i kalıcı olarak Object hale getirelim...
const color = new String('Black');
console.log(typeof color);

console.log("----------");

//bir string 'i kalıcı olarak Object hale getirelim...
const age = new Number(23);
console.log(typeof age);
```

![Untitled](Untitled%2029.png)

![Untitled](Untitled%2030.png)

# Kalıtım

```jsx
function Person (ad, soyad){
    this.ad = ad;
    this.soyad = soyad;
}

Person.prototype.selamVer = function(){
    return `Merhaba ben ${this.ad} ${this.soyad}`;
}

const emre = new Person('Emre', 'Altunbilek');
const hasan = new Person('Hasan', 'Yılmaz');

console.log(emre.selamVer());
console.log(hasan.selamVer());

function Ogrenci(ad, soyad, no){
    this.ad = ad;
    this.soyad = soyad;
    this.no = no;
}

Ogrenci.prototype.selamVer = function(){
    return `Merhaba ben ${this.no} numaralı öğrenci ${this.ad} ${this.soyad}`;
}

const serkan = new Ogrenci('Serkan','IŞIK', 1810206031);

console.log(serkan.selamVer());
```

![Untitled](Untitled%2031.png)

```jsx
function Person (ad, soyad){
    this.ad = ad;
    this.soyad = soyad;
}

Person.prototype.selamVer = function(){
    return `Merhaba ben ${this.ad} ${this.soyad}`;
}

const emre = new Person('Emre', 'Altunbilek');
const hasan = new Person('Hasan', 'Yılmaz');

console.log(emre.selamVer());
console.log(hasan.selamVer());

function Ogrenci(ad, soyad, no){
    Person.call(this, ad, soyad);
    this.no = no;
}

Ogrenci.prototype.selamVer = function(){
    return `Merhaba ben ${this.no} numaralı öğrenci ${this.ad} ${this.soyad}`;
}

const serkan = new Ogrenci('Serkan','IŞIK', 1810206031);

console.log(serkan.selamVer());
```

![Untitled](Untitled%2031.png)

```jsx
function Person (ad, soyad){
    this.ad = ad;
    this.soyad = soyad;
}

Person.prototype.selamVer = function(){
    return `Merhaba ben ${this.ad} ${this.soyad}`;
}

const emre = new Person('Emre', 'Altunbilek');
const hasan = new Person('Hasan', 'Yılmaz');

console.log(emre.selamVer());
console.log(hasan.selamVer());

function Ogrenci(ad, soyad, no){
    Person.call(this, ad, soyad);
    this.no = no;
}

Ogrenci.prototype = Object.create(Person.prototype);

/*Prototype ‘ların nesne döndürdüğünü biliyoruz Ogrenci.prototype'ın döndereceği 
nesne artık Person.prototype olacak*/

/*
Ogrenci.prototype.selamVer = function(){
    return `Merhaba ben ${this.no} numaralı öğrenci ${this.ad} ${this.soyad}`;
}
*/

const serkan = new Ogrenci('Serkan','IŞIK', 1810206031);

console.log(serkan.selamVer());
console.log(serkan.no);
```

![Untitled](Untitled%2032.png)

```jsx
function Person (ad, soyad){
    this.ad = ad;
    this.soyad = soyad;
}

Person.prototype.selamVer = function(){
    return `Merhaba ben ${this.ad} ${this.soyad}`;
}

const emre = new Person('Emre', 'Altunbilek');
const hasan = new Person('Hasan', 'Yılmaz');

console.log(emre.selamVer());
console.log(hasan.selamVer());

function Ogrenci(ad, soyad, no){
    Person.call(this, ad, soyad);
    this.no = no;
}

Ogrenci.prototype = Object.create(Person.prototype);

//overwrite yapılabilir
Ogrenci.prototype.selamVer = function(){
    return `Merhaba ben ${this.no} numaralı öğrenci ${this.ad} ${this.soyad}`;
}

const serkan = new Ogrenci('Serkan','IŞIK', 1810206031);

console.log(serkan.selamVer());
console.log(serkan.no);
```

![Untitled](Untitled%2033.png)

```jsx
function Person (ad, soyad){
    this.ad = ad;
    this.soyad = soyad;
}

Person.prototype.selamVer = function(){
    return `Merhaba ben ${this.ad} ${this.soyad}`;
}

const emre = new Person('Emre', 'Altunbilek');
const hasan = new Person('Hasan', 'Yılmaz');

console.log(emre.selamVer());
console.log(hasan.selamVer());

function Ogrenci(ad, soyad, no){
    Person.call(this, ad, soyad);
    this.no = no;
}

Ogrenci.prototype = Object.create(Person.prototype);

//overwrite yapılabilir
Ogrenci.prototype.selamVer = function(){
    return `Merhaba ben ${this.no} numaralı öğrenci ${this.ad} ${this.soyad}`;
}

Ogrenci.prototype.numaraSoyle = function(){
    return `Benim okul numaram ${this.no}`;
}

const serkan = new Ogrenci('Serkan','IŞIK', 1810206031);

console.log(serkan.selamVer());
console.log(serkan.numaraSoyle());
```

![Untitled](Untitled%2034.png)

---

### Array’den Kalıtım Yapma

```jsx
function MyArray(){

}

const myArray = new MyArray();

console.log(myArray);
```

![Untitled](Untitled%2035.png)

```jsx
function MyArray(){

}

MyArray.prototype = Object.create(Array.prototype);

const arr = new MyArray();

console.log(arr);
```

![Untitled](Untitled%2036.png)

```jsx
function MyArray(){

}

MyArray.prototype = Object.create(Array.prototype);

const arr = new MyArray();

arr.push(17);
arr.push('Serkan');
arr.push(true);

console.log(arr);
```

![Untitled](Untitled%2037.png)

### Keni Oluşturduğumuz map fonksiyonunu Array yapısına ekleme

```jsx
//map
const myArray = [1, 2, 3, 4, 5];

const newArray = myArray.map(function (value) {
    return value * 2; //return is mandatory
		//value: dizinin mevcut indisindeki değeri temsil eder    
});

console.log(newArray);

console.log("----------");

//kendimize ait map
function myMap (array, callBack) {
    const tempArray = [];
    for (let i = 0; i < array.length; i++) {
        tempArray.push(callBack(array[i]))     
    }
    return tempArray;
}
 
const secondNewArray = myMap(myArray, function myCallBack(value){
    return value * 2;
});

console.log(secondNewArray);
```

![Untitled](Untitled%2038.png)

```jsx
Array.prototype.myMap = function  (callBack) {
    const tempArray = [];
    /* this.length --> O an bu fonksiyonu çağıran dizinin boyutu*/
    for (let i = 0; i < this.length; i++) {
        tempArray.push(callBack(this[i]))     
    }
    return tempArray;
}

const myArray = [1, 2, 3, 4, 5];

const newArray = myArray.myMap(function (value) {
    return value * 2; 
});

console.log(newArray);

const secondNewArray = myArray.map(function (value) {
    return value * 2; 
});

console.log(secondNewArray);
```

![Untitled](Untitled%2039.png)

<aside>

💡 myMap artık bütün Array ‘ler tarafından kullanılabilir. Çünkü bu yapı artık bütün Array ‘lere ait.

</aside>