<div class="header">
  <br />
  <br />
  <br />
  <h1 class="title">Bulletin Board</h1>
  <h2 class="description">Inkubation software for connecting<br />social groups large and small.</h2>
  <br />
  <br />
  <br />
  <div class="browser">
    <div class="toolbar">
      <div class="column left">
        <span class="dot" style="background:#ED594A;"></span>
        <span class="dot" style="background:#FDD800;"></span>
        <span class="dot" style="background:#5AC05A;"></span>
      </div>
      <div class="column middle">
        <input type="text" value="https://demo.communityfolder.com">
      </div>
      <div class="column right">
        <div style="float:right">
          <span class="bar"></span>
          <span class="bar"></span>
          <span class="bar"></span>
        </div>
      </div>
    </div>
  
    <div class="content">
      <div id="wrap">
        <iframe id="frame" title="demo" src="https://demo.communityfolder.com" frameborder="0"></iframe>
      </div>
    </div>
  </div>
</div>

<div class="panel">
  <div class="container">
    <a class="waves-effect waves-light btn white black-text">main</a>
    <a class="waves-effect waves-light btn grey">forums</a>
    <a class="waves-effect waves-light btn grey">topics</a>
    <a class="waves-effect waves-light btn grey">posts</a>
    <a class="waves-effect waves-light btn grey">profiles</a>
    <a class="waves-effect waves-light btn grey">storefronts</a>
    <a class="waves-effect waves-light btn grey">events</a>
    <a class="waves-effect waves-light btn grey">calendar</a>
    <a class="waves-effect waves-light btn grey">results</a>
    <a class="waves-effect waves-light btn grey">profiles</a>
    <a class="waves-effect waves-light btn grey">storefronts</a>
    <a class="waves-effect waves-light btn grey">events</a>
    <a class="waves-effect waves-light btn grey">calendar</a>
    <a class="waves-effect waves-light btn grey">results</a>
  </div>
</div>

<style>
  .header {
    background: #aaa;
  }

  .title {
    font-weight: 900;
    color: #000;
    font-size: 3em;
    margin: 0;
    text-align: center;
  }

  .description {
    color: #000;
    font-size: 2.5em;
    margin: 0;
    text-align: center;
  }

  /* The browser window */
  .browser {
    background: #eee;
    border: 3px solid #f1f1f1;
    border-top-left-radius: 4px;
    border-top-right-radius: 4px;
    border-bottom: 0;
    max-width: 900px;
    margin: 0 auto;
  }
  
  /* Container for columns and the top "toolbar" */
  .toolbar {
    padding: 12px 10px 0 10px;
    background: #f1f1f1;
    border-top-left-radius: 4px;
    border-top-right-radius: 4px;
  }
  
  /* Create three unequal columns that floats next to each other */
  .column {
    float: left;
  }
  
  .left {
    width: 15%;
  }
  
  .right {
    width: 10%;
  }
  
  .middle {
    width: 75%;
  }
  
  /* Clear floats after the columns */
  .toolbar:after {
    content: "";
    display: table;
    clear: both;
  }
  
  /* Three dots */
  .dot {
    margin-top: 4px;
    height: 12px;
    width: 12px;
    background-color: #bbb;
    border-radius: 50%;
    display: inline-block;
  }
  
  /* Style the input field */
  input[type=text] {
    width: 100%;
    border-radius: 3px;
    border: none;
    background-color: white;
    margin-top: -8px;
    height: 25px;
    color: #666;
    padding: 5px;
  }
  
  /* Three bars (hamburger menu) */
  .bar {
    width: 17px;
    height: 3px;
    background-color: #aaa;
    margin: 3px 0;
    display: block;
  }
  
  /* Page content */
  .content {
    background: #fff;
    padding: 0;
    overflow: hidden;
  }

  #wrap {
    width: 900px;
    height: 490px;
    padding: 0;
    overflow: hidden; 
  }
  #frame {
    width: 1200px;
    height: 660px;
    border: 0;
  }
  #frame {
    -ms-zoom: 0.75;
    -moz-transform: scale(0.75);
    -moz-transform-origin: 0 0;
    -o-transform: scale(0.75);
    -o-transform-origin: 0 0;
    -webkit-transform: scale(0.75);
    -webkit-transform-origin: 0 0;
  }


  .panel {
    padding: 2em;
    text-align: center;
    background: #000;
  }

  .panel a {
    margin: 0.2em;
  }
</style>