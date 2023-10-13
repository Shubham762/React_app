# React_app
Food application

APi with alert to click

import React, { useState, useEffect } from 'react';
import './style.css';

export default function App() {
  const [data, setData] = useState([]);
  const [altdata,setAltdata]=useState('');
  useEffect(() => {
    getData();
  }, []);
  const getData = async () => {
    const datajson = await fetch(
      'https://jsonplaceholder.typicode.com/comments'
    );
    const json = await datajson.json();
    //  console.log(json);
    setData(json);
  };
  const handleClick = (item) => {
       setAltdata(item);
   // console.log('Inside handleClick',item,altdata);
     alert("Hi"+" "+`${item}`);
   
  };

  return (
    <div>
      <h1>API calling</h1>
      {data.map((item) => {
        return (
          <div>
     
            <li
              onClick={(props) => {
                handleClick(item.email);
               //alert("HI",props.item.email)
              }}
            >
              {item.email}
            </li>
          </div>
        );
      })}
    </div>
  );
}

