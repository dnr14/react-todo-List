# 1. TodoList μ΄ν΄λ³΄κΈ° π

<p align=center style="color:#b9b9b9">νλ‘μ νΈ κΈ°κ° 2021.07.22 ~ 2021.07.26</p>

### π₯ μλΉμ€ μκ°

 <h4>μ€λ ν΄μΌ νλ μΌμ κ°λ¨ν μ μ΄ λμ μ μλ μΉμ±μλλ€.</h4>

### β­οΈ μ£Όμ κΈ°λ₯

- λ©λͺ¨λ μ΅λ 10κ°κΉμ§ μλ ₯ κ°λ₯ν©λλ€.
- μλ£λ μΌμ μ­μ ν  μ μμ΅λλ€.
- μ μ λ©λͺ¨λ μ¬μ©μκ° μ­μ νκΈ° μ κΉμ§λ μμ΄μ§μ§ μμ΅λλ€.

### π» κΈ°μ  μ€ν

- `TypeScript`
- `React`
- `Styled-components`
- `crypto-js`

> #### π νλ‘μ νΈ κ΅¬μ‘°

```ts
ββcomponent  // UIλ₯Ό κ΅¬μ±νλ μ»΄ν¬λνΈλ€μ΄ μλ ν΄λμλλ€.
ββhelpers    // μ νΈν¨μκ° λͺ¨μ¬μλ ν΄λμλλ€.
ββtypes      // νμμ μ μν΄λμ ν΄λμλλ€.
```

> #### β νλ‘μ νΈ μ€ν ν΄λ³΄κΈ°

```js
mkdir todoList
cd todoList
git clone https://github.com/dnr14/React-Todo-List.git
npm -g i serve
npm install
npm run build
serve build
λΈλΌμ°μ  localhost:3000 μ μ
```

> #### π¨βπ» κ΅¬ννλ©΄

- [μ²΄ννκΈ°](https://dnr14.github.io/todoList)

<div align=center>
  <img src='./public/images/todoList.gif' />
</div>

<br>

### π₯ ν΅μ¬ κΈ°λ₯ μ€λͺ

1.  μλ²μ DBλ₯Ό μ΄μ©νμ§ μμμ λ¦¬μ€νΈ μ μ₯μ λ‘μ»¬μ€ν λ¦¬μ§λ₯Ό μ΄μ©νμ΅λλ€. μ¬μ©μκ° λ¦¬μ€νΈλ₯Ό μμ±ν  λ λ§λ€ μ μ₯νλ κ±΄ λΆνμνλ€λ μκ°μ΄ λ€μ΄μ λΈλΌμ°μ λ₯Ό μ΄ννμ λ λ‘μ»¬μ€ν λ¦¬μ§μ μ μ₯ν©λλ€.

```ts
useEffect(() => {
  // λ‘μ»¬μ€ν λ¦¬μ§κ° μμΌλ©΄ μμ±μνλ€.
  if (!hasKeys(LOCALSTORAGE_NAME)) {
    makeLocalStorage();
  }

  const handleBeforeUnload = () => {
    const encodedArray = encrypt(todoArray, SECRET_KEY);
    setItem(LOCALSTORAGE_NAME, encodedArray);
  };

  // μ μ κ° λΈλΌμ°μ λ₯Ό μ΄ννλ©΄ λ‘μ»¬μ€ν λ¦¬μ§μ μμ±ν λ¦¬μ€νΈλ₯Ό μ μ₯νλ€.
  window.addEventListener("beforeunload", handleBeforeUnload);
}, [todoArray, makeLocalStorage]);
```

2.  λ‘μ»¬μ€ν λ¦¬μ§μ μ μ₯λ λ΄μ©μ λ€λ₯Έ μ¬λλ€μ΄ λ³Ό μ μλλ‘ Cyroto λͺ¨λμ ν΅ν΄ μνΈνλ₯Ό νμ΅λλ€. AES λμΉ­ν€ μνΈνμ νμν ν€ κ°μ νκ²½λ³μμμ κ΄λ¦¬λ₯Ό ν©λλ€.

```ts
const handleBeforeUnload = () => {
  const encodedArray = encrypt(todoArray, SECRET_KEY);
  setItem(LOCALSTORAGE_NAME, encodedArray);
};

// .env
// REACT_APP_SECRET_KEY=secret-key-1;
```
