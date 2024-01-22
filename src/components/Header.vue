<template>
<div>
  <div class="header">
      <div class="header-content-left">
        <span>Expense Tracker</span>
      </div>
      <div class="header-content-right">
        <a href="https://github.com/banuaggun/expense-tracker" rel="noreferrer noopener" target="_blank" className="header-item social">
          Project Repository
        </a>
        <a href="https://portfolio-banuaggun.vercel.app/" rel="noreferrer noopener" target="_blank" className="header-item social">
          Portfolio
        </a>
      </div>
  </div>
  <div class="header-mobile">
      <div class="header-mobile-content-top">
        <span>Expense Tracker</span>
      </div>
      <div class="header-mobile-content-bottom">
        <a href="https://github.com/banuaggun/expense-tracker" rel="noreferrer noopener" target="_blank" className="header-item social">
          Project Repository
        </a>
        <a href="https://portfolio-banuaggun.vercel.app/" rel="noreferrer noopener" target="_blank" className="header-item social">
          Portfolio
        </a>
      </div>
  </div>
  </div>
</template>
<style>
span, a{
  color:#121212;
}
.header{
  display: none;
}
.header,
.header-mobile{
  background-color:snow;
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.3);
  color:#121212;
  font-family:'Lora', sans-serif;
}
.header-content-left span,
.header-mobile-content-top span{
  font-weight:600;
  text-transform: uppercase;
}
.header-content-right a,
.header-mobile-content-bottom a{
  font-weight:400;
  border-bottom:3px solid transparent;
  width:max-content;
}
.header-mobile{
  display:block;
  height:80px;
  position:sticky;
}
.header-mobile-content-top{
  width:100%;
  height:40px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.header-mobile-content-top span{
  font-size:18px; 
}
.header-mobile-content-bottom{
  width:100%;
  height:40px;
  display:flex;
  align-items: center;
  justify-content: flex-end;
}
.header-mobile-content-bottom a{
  padding-right:20px;
  font-size:14px;
}
.header-content-right a:hover{
  border-bottom:3px solid blue;
}
@media only screen and (min-width:700px) and (max-width:1940px){
  .header-mobile{
    display:none;
  }
  .header{
    display:block;
    height:80px;
    position:sticky;
    display:flex;
    justify-content: space-between;
  }
   .header-content-left{
    display:flex;
    align-items:center;
  }
  .header-content-right{
    display:flex;
    align-items:flex-end;
    margin-bottom:10px;
  }
}
@media only screen and (min-width:700px) and (max-width:1100px){
  .header-content-left span{
    padding-left:40px;
    font-size:20px;
  }
  .header-content-right a{
    padding-right:20px;
    font-size:16px;
  }
}
@media only screen and (min-width:1101px) and (max-width:1400px){
  .header-content-left span{
    padding-left:40px;
    font-size:28px;
  }
  .header-content-right a{
    margin-right:20px;
    font-size:18px;
  }
}
@media only screen and (min-width:1401px) and (max-width:1940px){
  .header-content-left span{
    padding-left:100px;
    font-size:28px;
  }
  .header-content-right{
    padding-right:100px;
  }
  .header-content-right a{
    margin-right:20px;
    font-size:18px;
  }
}
</style>
