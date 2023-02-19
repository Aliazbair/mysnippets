---
title: Navbar Components
slug: navbar-components
excerpt: may navbar Components
author: ali
image: 'https://cdn.static-economist.com/sites/default/files/images/2015/09/blogs/economist-explains/code2.png'
---

# navbar one

```jsx
import { useState } from 'react';
import { close, logo, menu } from '../assets';

import { navLinks } from '../constants';

const Navbar = () => {
  const [active, setActive] = useState('Home');
  const [toggle, setToggle] = useState(false);
  return (
    <nav className='w-full flex py-6 justify-between items-center navbar'>
      <img src={logo} alt='logo' className='w-[124px] h-[32px]' />

      {/* desktop menu */}
      <ul className='list-none sm:flex hidden justify-end items-center flex-1'>
        {navLinks.map((nav, index) => (
          <li
            key={index}
            className={`font-poppins font-normal cursor-pointer text-[16px] ${
              active === nav.title
                ? 'text-slate-200 bg-blue-600 px-2 rounded'
                : 'text-dimWhite'
            } ${index === navLinks.length - 1 ? 'mr-0' : 'mr-10'} `}
            onClick={() => setActive(nav.title)}
          >
            <a href={`#${nav.id}`}>{nav.title}</a>
          </li>
        ))}
      </ul>

      {/* menu in mobile */}
      <div className='sm:hidden flex flex-1 justify-end items-center'>
        <img
          src={menu}
          alt='menu'
          className='w-[28px] h-[28px] object-contain '
          onClick={() => setToggle(!toggle)}
        />

        <div
          className={`${
            !toggle ? 'hidden' : 'flex'
          } p-6 bg-black-gradient absolute top-20 right-0 mx-4 my-2 min-w-[140px] rounded-xl sidebar `}
        >
          <ul className='list-none flex justify-end items-start flex-1 flex-col'>
            {navLinks.map((nav, index) => (
              <li
                key={index}
                className={`font-poppins font-normal cursor-pointer text-[16px] ${
                  active === nav.title ? 'text-slate-600 ' : 'text-dimWhite'
                } ${index === navLinks.length - 1 ? 'mr-0' : 'mr-10'} `}
                onClick={() => setActive(nav.title)}
              >
                <a href={`#${nav.id}`}>{nav.title}</a>
              </li>
            ))}
          </ul>
        </div>
      </div>
    </nav>
  );
};

export default Navbar;
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
