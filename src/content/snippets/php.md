---
title: PHP
slug: php
excerpt: React Components 
author: ali
image: 'https://cdn.static-economist.com/sites/default/files/images/2015/09/blogs/economist-explains/code2.png'
---


# create text component

```jsx
const Text = ({ children, className }) => {
  return (
    <h1 class='text-4xl font-bold uppercase'>
      <span
        class={` ${className} bg-clip-text text-transparent bg-gradient-to-r from-red-500 via-yellow-500 to-blue-500`}
      >
        {children}
      </span>
    </h1>
  );
};

export default Text;
```

## create Card Component with grid

```jsx
function Card({ children, className }) {
  return (
    <div className={`py-4 grid gap-4 md:grid-cols-2 ${className}`}>
      {children}
    </div>
  );
}

export default Card;
```

## create input component

```jsx
import React from 'react';

export const Input = ({ type, name, handleChange, value, placeholder }) => {
  return (
    <input
      type={type}
      name={name}
      className='shadow border text-gray-700 rounded py-2 px-3 form-input mt-1 block w-full ring-yellow-500 focus:ring outline-none'
      value={value}
      onChange={handleChange}
      placeholder={placeholder}
    />
  );
};
```


## create Navbar component

```jsx
import { useSelector, useDispatch } from 'react-redux';
import { Link } from 'react-router-dom';
import { logout } from '../redux/auth/authSlice';

const Links = [
  {
    name: 'Home',
    url: '/',
  },

  {
    name: 'Brokers',
    url: '/brokers',
  },
  {
    name: 'Missions',
    url: '/missions',
  },
  {
    name: 'Property',
    url: '/property',
  },
  {
    name: 'Snippets',
    url: '/snippets',
  },
];

export default function Navbar() {
  const { user } = useSelector((state) => state.auth);
  const dispatch = useDispatch();
  const products = useSelector((state) => state.card.products);
  return (
    <nav className='fixed top-0 w-full flex justify-between items-center px-10 bg-slate-700 text-gray-300 py-2'>
      <div>
        <h3 className='text-xl text-yellow-500 font-bold'>Ali Auth</h3>
      </div>
      <ul className='flex items-center space-x-4'>
        {user ? (
          <div className='flex space-x-2'>
            <h2 className='font-bold text-orange-300 cursor-pointer'>
              {user?.user.name}
            </h2>
            {Links.map(({ name, url }) => (
              <>
                <Link key={name} to={url}>
                  {name}
                </Link>
              </>
            ))}
            <button
              className='text-indigo-500'
              onClick={() => dispatch(logout())}
              type='button'
            >
              logout
            </button>
          </div>
        ) : (
          <div className='flex space-x-3'>
            <Link to='/login' className='hover:text-gray-200'>
              Login
            </Link>
            <Link to='/register' className='hover:text-gray-200'>
              Register
            </Link>
          </div>
        )}

        <Link to='/cart' className='hover:text-gray-200'>
          <div className='relative'>
            <img className='w-10' src='/green-shopping-cart-10909.svg' alt='' />
            <span className='absolute top-1 right-0 font-bold bg-red-600 animate-pulse rounded-full px-2 py-0.5  text-sm grid place-items-center'>
              {products.length}
            </span>
          </div>
        </Link>
      </ul>
    </nav>
  );
}


```
