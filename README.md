# React_app
Food application

1====>APi with alert to click

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


2===============>


import React, { useState, useEffect } from 'react';
import './style.css';

export default function App() {
  const [fnametxt, setFnametxt] = useState('');
  const [snametxt, setSnametxt] = useState('');
  const [emailtxt, setEmailtxt] = useState('');
  // const [obj,setObj]=useState({});
   const [dataobj,setDataobj]=useState([]);
  let obj={};
  var data=[];


  const handleClick=()=>{
       obj['fname']=fnametxt
       obj['sname']=snametxt
       obj['email']=emailtxt
       console.log("",obj);
       data.push(obj)
       setDataobj(data);
       console.log("",data);
  }
 

  return (
    <div>
      <h1>API calling</h1>
     <input 
     placeholder="Enter the first name"
     value={fnametxt}
     onChange={(e)=>{setFnametxt(e.target.value)}}
     
     />
     <input placeholder="Enter the second name"
      value={snametxt}
      onChange={(e)=>{setSnametxt(e.target.value)}}/>
     <input placeholder="Enter the email"
      value={emailtxt}
      onChange={(e)=>{setEmailtxt(e.target.value)}}
     />
     <div></div>
     <button onClick={()=>{handleClick()}}>Add</button>
     {
       dataobj.map((item)=>{
         return(
           <div>
            <table>
             <tr>
               <th>FirstName</th>
               <th>SecondName</th>
               <th>Email</th>
             </tr>
             <tr>
               <td>{item.fname}</td>
               <td>{item.sname}</td>
               <td>{item.email}</td>
             </tr>

            </table>
             
           </div>
         )
       })
     }
    </div>
  );
}


3.===========================>
Print name using recursion
var str="shubham"
var len=str.length;
var i=0


function print(str,i){
    if(i===len) return;
      console.log(str[i]);
        i++;
    print(str,i);
}

print(str,i)


