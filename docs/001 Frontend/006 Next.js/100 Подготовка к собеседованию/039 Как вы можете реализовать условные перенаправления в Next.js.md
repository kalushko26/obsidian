---
title: Как вы можете реализовать условные перенаправления в Next.js на основе определенных критериев, таких как статус аутентификации пользователя или его роль?
draft: false
tags:
  - NextJS
  - Authentication
  - getServerSideProps
  - getStaticProps
  - useEffect
  - router
info:
  - https://cheatcode.co/blog/how-to-handle-authenticated-routes-with-next-js
---
  Вот несколько методов для реализации условных перенаправлений в Next.js на основе таких критериев, как статус аутентификации пользователя или его роль:

***1. Перенаправления в*** `getServerSideProps` ***или*** `getStaticProps`

- Проверьте условия внутри этих функций и инициируйте перенаправления с помощью **`res.writeHead()`** и **`res.end()`:

```JavaScript
export async function getServerSideProps(context) { 
	const isAuthenticated = await checkAuth(context.req); 
	
	if ( !isAuthenticated && context.resolvedUrl !== '/login' ){ 
		context.res .writeHead(302, { Location: '/login' }); 
		context.res.end(); 
		
		return { props: {} }; 
	} 
		
	// ...получение данных для аутентифицированных пользователей... 
}`
```

***2. Перенаправления на стороне клиента с*** `useEffect` ***и*** `router.push`:

- Выполните перенаправления на стороне клиента после рендеринга компонента:

```JavaScript

 import { useEffect } from 'react'; 
 import { useRouter } from 'next/router'; 
 
 function MyPage() { 
	 const router = useRouter(); 
	 useEffect( () => { 
		 const isAuthenticated = checkAuth();
		 if (!isAuthenticated) { 
			 router.push('/login'); 
		}
	}, []); 

// ...содержимое страницы... 
}
```

___

[[006 Next.js|Назад]]