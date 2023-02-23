---
title: create hood landing page
slug: hood-website
excerpt: hood landing page
author: ali
image: 'https://cdn.static-economist.com/sites/default/files/images/2015/09/blogs/economist-explains/code2.png'
---

# first install react app

```code
npx create-react-app
```

# create components folder and setup app.js

```jsx
import styles from './style';
import {
  Billing,
  Business,
  CardDeal,
  Clients,
  CTA,
  Footer,
  Hero,
  Navbar,
  Stats,
  Testimonials,
} from './components';
import Applaction from './components/Applaction';
const App = () => (
  <div className='bg-primary w-full overflow-hidden'>
    {/* navbar */}
    <div className={`${styles.paddingX} ${styles.flexCenter}`}>
      <div className={`${styles.boxWidth}`}>
        <Navbar />
      </div>
    </div>

    {/* hero */}
    <div className={`bg-primary ${styles.flexStart}`}>
      <div className={`${styles.boxWidth}`}>
        <Hero />
      </div>
    </div>

    {/* main content */}
    <main className={`bg-primary ${styles.paddingX}  ${styles.flexCenter}`}>
      <div className={`${styles.boxWidth}`}>
        <Stats />
        <Business />
        <Billing />
        <CardDeal />
        <Testimonials />
        <Clients />
        <CTA />
        <Applaction />
        <Footer />
      </div>
    </main>
  </div>
);

export default App;
```

### create Navbar

```js
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

### create Hero

```js
import styles from '../style';
import { discount, robot } from '../assets';
import GetStarted from './GetStarted';
const Hero = () => {
  return (
    <section
      id='home'
      className={`flex flex-col md:flex-row ${styles.paddingY}`}
    >
      {/* left */}
      <div
        className={`flex-1 ${styles.flexStart} flex-col xl:px-0 sm:px-16 px-6`}
      >
        {/* discount */}
        <div className='flex flex-row items-center py-[6px] px-4 bg-discount-gradient rounded-[10px] mb-2'>
          <img src={discount} alt='discount' className='w-[32px] h-[32]' />
          <p className={`${styles.paragraph} ml-2`}>
            <span className='text-white'>20%</span> Discount For
            <span className='text-white'>1 Month</span>Account
          </p>
        </div>
        <div className='flex flex-row justify-between items-center w-full'>
          <h1 className='flex-1 font-poppins font-semibold ss:text[72px] text-[52px] text-white ss:leading-[100.8px] leading-[75px]'>
            The Next <br className='sm:block hidden' />
            <span className='text-gradient'>Generation</span>
          </h1>

          <div className='ss:flex hidden md:mr-4 mr-0'>
            <GetStarted />
          </div>
        </div>

        <h1 className='font-poppins font-semibold text-white ss:text-[68px] text-[52px] ss:leading-[100.8px] leading-[75px] w-full'>
          Payment Method.
        </h1>
        <p className={`${styles.paragraph} max-w-[470px] mt-5`}>
          Our team of experts uses a methodology to identify the credit cards
          most likely to fit your needs. We examine annual percentage rates,
          annual fees.
        </p>
      </div>

      {/*  */}
      <div
        className={`flex-1 flex ${styles.flexCenter} md:my-0 my-10 relative `}
      >
        <img
          src='https://res.cloudinary.com/dy9idapqa/image/upload/v1677155326/Ai/pre-footer-new-image_qacvxo.webp'
          alt='billing'
          className='w-[100%] h-[100%] relative z-[5]'
        />
        {/* <img
          src={robot}
          alt='billing'
          className='w-[100%] h-[100%] relative z-[5]'
        /> */}
        {/* gradient start */}
        <div className='absolute z-[0] w-[40%] h-[35%] top-0 pink__gradient' />
        <div className='absolute z-[1] w-[80%] h-[80%] rounded-full white__gradient' />
        <div className='absolute z-[0] w-[50%] h-[50%] right-20 bottom-20 blue__gradient' />
      </div>

      {/*  */}
      <div className={`ss:hidden ${styles.flexCenter}`}>
        <GetStarted />
      </div>
    </section>
  );
};

export default Hero;
```

## create Stats

```js
import { stats } from '../constants';
import styles from '../style';
const Stats = () => {
  return (
    <section
      className={`${styles.flexCenter} flex-row flex-wrap sm:mb-20 mb-6`}
    >
      {stats.map((stat) => (
        <div
          key={stat.id}
          className={`flex-1 flex justify-start items-center flex-row m-3 `}
        >
          <h4 className='font-poppins font-semibold xs:text-[40.89px] text-[30.89px] xs:leading-[53.16px] leading-[43.16px] text-white'>
            {stat.value}
          </h4>
          <p className='font-poppins font-normal xs:text-[20.45px] text-[15.45px] xs:leading-[26.58px] leading-[21.58px] text-gradient uppercase ml-3'>
            {stat.title}
          </p>
        </div>
      ))}
    </section>
  );
};

export default Stats;
```

## create Business

```js
import { features } from '../constants';
import styles, { layout } from '../style';
import Button from './Button';

const FeatureCard = ({ icon, title, content, index }) => (
  <div
    className={`flex flex-row p-6 rounded-[20px] ${
      index !== features.length - 1 ? 'mb-6' : 'mb-0'
    } feature-card`}
  >
    <div
      className={`w-[64px] h-[64px] rounded-full ${styles.flexCenter} bg-dimBlue`}
    >
      <img src={icon} alt='start' className='w-[50%] h-[50%] object-contain' />
    </div>
    <div className='flex-1 flex flex-col ml-3'>
      <h4 className='text-white font-poppins font-semibold text-[18px] leading-[23.4px] mb-1'>
        {title}
      </h4>
      <p className='font-poppins font-normal text-dimWhite text-[16px] leading-[24px]'>
        {content}
      </p>
    </div>
  </div>
);
const Business = () => {
  return (
    <section id='features' className={`${layout.section}`}>
      {/* text */}
      <div className={layout.sectionInfo}>
        <h2 className={styles.heading2}>
          your do the business
          <br className='sm:block hidden' />
          well handle the mony
        </h2>
        <p className={`${styles.paragraph} max-w-[470px] mt-5`}>
          With the right credit card, you can improve your financial life by
          building credit, earning rewards and saving money. But with hundreds
          of credit cards on the market.
        </p>
        <Button styles={`mt-10`} />
      </div>

      {/* image */}
      <div>
        {features.map((f, index) => (
          <FeatureCard key={f.id} {...f} index={index} />
        ))}
      </div>
    </section>
  );
};

export default Business;
```

## create Billing

```js
import { apple, bill, google } from '../assets';
import styles, { layout } from '../style';
const Billing = () => {
  return (
    <section id='product' className={layout.sectionReverse}>
      {/* left */}
      <div className={layout.sectionImgReverse}>
        <img
          src='https://res.cloudinary.com/dy9idapqa/image/upload/v1677155326/Ai/start-new-image-2_vr6n1h.webp'
          alt=''
          className='w-[100%] h-[100%] relative z-[5]'
        />
        {/* <img src={bill} alt='' className='w-[100%] h-[100%] relative z-[5]' /> */}
        {/* gradient start */}
        <div className='absolute z-[3] -left-1/2 top-0 w-[50%] h-[50%] rounded-full white__gradient' />
        <div className='absolute z-[0] w-[50%] h-[50%] -left-1/2 bottom-0 rounded-full pink__gradient' />
        {/* gradient end */}
      </div>
      {/* right */}
      <div className={layout.sectionInfo}>
        <h2 className={styles.heading2}>
          Easily control your <br className='sm:block hidden' /> billing &
          invoicing
        </h2>
        <p className={`${styles.paragraph} max-w-[470px] mt-5`}>
          Elit enim sed massa etiam. Mauris eu adipiscing ultrices ametodio
          aenean neque. Fusce ipsum orci rhoncus aliporttitor integer platea
          placerat.
        </p>
        <div className='flex flex-row flex-wrap sm:mt-10 mt-6'>
          <img
            src={apple}
            alt='google_play'
            className='w-[128.86px] h-[42.05px] object-contain mr-5 cursor-pointer'
          />
          <img
            src={google}
            alt='google_play'
            className='w-[144.17px] h-[43.08px] object-contain cursor-pointer'
          />
        </div>
      </div>
    </section>
  );
};

export default Billing;
```

## create CardDeal

```js
import { card } from '../assets';
import styles, { layout } from '../style';
import Button from './Button';
const CardDeal = () => {
  return (
    <section className={layout.section}>
      <div className={layout.sectionInfo}>
        <h2 className={styles.heading2}>
          Find a better card deal <br className='sm:block hidden' /> in few easy
          steps.
        </h2>
        <p className={`${styles.paragraph} max-w-[470px] mt-5`}>
          Arcu tortor, purus in mattis at sed integer faucibus. Aliquet quis
          aliquet eget mauris tortor.ç Aliquet ultrices ac, ametau.
        </p>

        <Button styles={`mt-10`} />
      </div>

      <div className={layout.sectionImg}>
        <img src={card} alt='billing' className='w-[100%] h-[100%]' />
      </div>
    </section>
  );
};

export default CardDeal;
```

## create Testimonials

```js
import { feedback } from '../constants';
import styles from '../style';
import FeedbackCard from './FeedbackCard';
const Testimonials = () => {
  return (
    <section
      id='clients'
      className={`${styles.paddingY} ${styles.flexCenter} flex-col relative `}
    >
      <div className='absolute z-[0] w-[60%] h-[60%] -right-[50%] rounded-full blue__gradient bottom-40' />

      <div className='w-full flex justify-between items-center md:flex-row flex-col sm:mb-16 mb-6 relative z-[1]'>
        <h2 className={styles.heading2}>
          What People are <br className='sm:block hidden' /> saying about us
        </h2>
        <div className='w-full md:mt-0 mt-6'>
          <p className={`${styles.paragraph} text-left max-w-[450px]`}>
            Everything you need to accept card payments and grow your business
            anywhere on the planet.
          </p>
        </div>
      </div>

      <div className='flex flex-wrap sm:justify-start justify-center w-full feedback-container relative z-[1]'>
        {feedback.map((card) => (
          <FeedbackCard key={card.id} {...card} />
        ))}
      </div>
    </section>
  );
};

export default Testimonials;
```

## create Clients

```js
import { clients } from '../constants';
import styles from '../style';
const Clients = () => {
  return (
    <section className={`${styles.flexCenter} my-4`}>
      <div className={`${styles.flexCenter} flex-wrap w-full`}>
        {clients.map((client) => (
          <div
            key={client.id}
            className={`flex-1 ${styles.flexCenter} sm:min-w-[192px] min-w-[120px] m-5`}
          >
            <img
              src={client.logo}
              alt='client_logo'
              className='sm:w-[192px] w-[100px] object-contain'
            />
          </div>
        ))}
      </div>
    </section>
  );
};

export default Clients;
```

## create CTA

```js
import styles from '../style';
import Button from './Button';
function CTA() {
  return (
    <section
      className={`${styles.flexCenter} ${styles.marginY} ${styles.padding} sm:flex-row flex-col bg-black-gradient-2 rounded-[20px] box-shadow`}
    >
      <div className='flex-1 flex flex-col'>
        <h2 className={styles.heading2}>Let’s try our service now!</h2>
        <p className={`${styles.paragraph} max-w-[470px] mt-5`}>
          Everything you need to accept card payments and grow your business
          anywhere on the planet.
        </p>
      </div>

      <div className={`${styles.flexCenter} sm:ml-10 ml-0 sm:mt-0 mt-10`}>
        <Button />
      </div>
    </section>
  );
}

export default CTA;
```

## create Applaction

```js
import { apple, bill, google } from '../assets';
import styles, { layout } from '../style';
const Applaction = () => {
  return (
    <section id='product' className={layout.sectionReverse}>
      {/* right */}
      <div className={layout.sectionInfo}>
        <h2 className={styles.heading2}>
          Easily control your <br className='sm:block hidden' /> billing &
          invoicing
        </h2>
        <p className={`${styles.paragraph} max-w-[470px] mt-5`}>
          Elit enim sed massa etiam. Mauris eu adipiscing ultrices ametodio
          aenean neque. Fusce ipsum orci rhoncus aliporttitor integer platea
          placerat.
        </p>
      </div>
      {/* left */}
      <div className={layout.sectionImgReverse}>
        <img
          src='https://res.cloudinary.com/dy9idapqa/image/upload/v1677155326/Ai/secure-backup_m3toqy.webp'
          alt=''
          className='w-[100%] h-[100%] relative z-[5]'
        />
        {/* <img src={bill} alt='' className='w-[100%] h-[100%] relative z-[5]' /> */}
        {/* gradient start */}
        <div className='absolute z-[3] -left-1/2 top-0 w-[50%] h-[50%] rounded-full white__gradient' />
        <div className='absolute z-[0] w-[50%] h-[50%] -left-1/2 bottom-0 rounded-full pink__gradient' />
        {/* gradient end */}
      </div>
    </section>
  );
};

export default Applaction;
```

## create Footer

```js
import styles from '../style';
import { logo } from '../assets';
import { footerLinks, socialMedia } from '../constants';

const Footer = () => {
  return (
    <section className={`${styles.flexCenter} ${styles.paddingY} flex-col`}>
      <div className={`${styles.flexStart} md:flex-row flex-col mb-8 w-full`}>
        <div className='flex-[1] flex flex-col justify-start mr-10'>
          <img
            src={logo}
            alt='hoobank'
            className='w-[266px] h-[72.14px] object-contain'
          />
          <p className={`${styles.paragraph} mt-4 max-w-[312px]`}>
            A new way to make the payments easy, reliable and secure.
          </p>
        </div>

        <div className='flex-[1.5] w-full flex flex-row justify-between flex-wrap md:mt-0 mt-10'>
          {footerLinks.map((footerlink) => (
            <div
              key={footerlink.title}
              className={`flex flex-col ss:my-0 my-4 min-w-[150px]`}
            >
              <h4 className='font-poppins font-medium text-[18px] leading-[27px] text-white'>
                {footerlink.title}
              </h4>
              <ul className='list-none mt-4'>
                {footerlink.links.map((link, index) => (
                  <li
                    key={link.name}
                    className={`font-poppins font-normal text-[16px] leading-[24px] text-dimWhite hover:text-secondary cursor-pointer ${
                      index !== footerlink.links.length - 1 ? 'mb-4' : 'mb-0'
                    }`}
                  >
                    {link.name}
                  </li>
                ))}
              </ul>
            </div>
          ))}
        </div>
      </div>

      <div className='w-full flex justify-between items-center md:flex-row flex-col pt-6 border-t-[1px] border-t-[#3F3E45]'>
        <p className='font-poppins font-normal text-center text-[18px] leading-[27px] text-white'>
          Copyright Ⓒ 2022 HooBank. All Rights Reserved.
        </p>

        <div className='flex flex-row md:mt-0 mt-6'>
          {socialMedia.map((social, index) => (
            <img
              key={social.id}
              src={social.icon}
              alt={social.id}
              className={`w-[21px] h-[21px] object-contain cursor-pointer ${
                index !== socialMedia.length - 1 ? 'mr-6' : 'mr-0'
              }`}
              onClick={() => window.open(social.link)}
            />
          ))}
        </div>
      </div>
    </section>
  );
};

export default Footer;
```
