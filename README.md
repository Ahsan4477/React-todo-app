# React-todo-app
ITs my First react todo app







(Page.js)

"use client"
import React, { useState } from 'react'

const page = () => {

  const [title, settitle] = useState()
  const [loss, setloss] = useState()
  const [mainwork, setmainwork] = useState([])
  const submithandler = (e) => {
    e.preventDefault()
    setmainwork([...mainwork, { title, loss }])

    settitle("")
    setloss('')
    console.log(mainwork)
  }

const deletehandler =  (i)=>{
   let copytask =[...mainwork]
   copytask.splice(i,1)
   setmainwork(copytask)
}
  
  let Showdisplay = <h2 className='flex  justify-center'>Empty here</h2>

  if (mainwork.length > 0) {
    Showdisplay = mainwork.map((t, i) => {
      return (
        <li key={i} className='flex items-center justify-between m-8'>
          <div className='flex items-center justify-between w-2/3'>
            <h3 className='text-2xl font-semibold'>{t.title}</h3>
            <h3 className='text-xl justify-center font-semibold'>{t.loss}</h3>
          </div>
           <button  
           onClick={()=>{
            deletehandler(i)
           }}
           className='bg-red-800 text-white px-4 py-2 rounded font-bold '>Remove</button>
        </li>
      )
    })
  }

  return (

    <>
      <div>
        <h1 className='bg-red-900 text-white p-5 text-5 text-5xl font-mono text-center'>Todo React</h1>

        <form onSubmit={submithandler}>
          <input type='text' className='text-2x1 border-zinc-800 border-4 m-2 px-4 py-2' placeholder='Click here' value={title}
            onChange={(e) => {
              settitle(e.target.value)
            }} />

          <input type='text' className='text-2x1 border-zinc-800 border-4 m-2 px-4 py-2' placeholder='Click here'value={loss}
            onChange={(e) => {
              setloss(e.target.value)
            }} />

          <button className='bg-blue-600 text-white py-3 px-5 text-2x1 font-light rounded m-3'>Add print</button>
        </form>
        <hr />
        <div>
          <ul className='bg-slate-400 p-8'>
            {Showdisplay}
          </ul>
        </div>
      </div>


    </>
  )
}

export default page
