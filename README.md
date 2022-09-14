# Discount Drug Network Embed Instructions
Thank you for using Discount Drug Network Plus! Here are the instructions and things to note while setting it up. 

## Head section
Please insert this CSS code before the closing `</head>` tag. 
```
<style>
   #iframe__container {
     display: flex;
     align-items: center;
     justify-content: center;
     width: 100%;
     margin-top: 4rem;
   }
   #ddn-iframe {
     padding: 0;
     width: 100%;
     border: 0px solid #E9E9E9;
     box-sizing: content-box;
     overflow: hidden;
     min-height:450px;
     min-width:375px;
   }
 </style> 
```

## Widget HTML
Next, please paste this code wherever you want your DDN+ widget to display.

```
<div id="iframe__container">
   <iframe id="ddn-iframe" src="https://discountdrugnetwork.com/?iframe=true" scrolling="no"></iframe>
</div>
```

**Note: The development iFrame is password protected. Please use these logins:**
`ddndev`
`discountdrugnetwork`

## JavaScript
Place this code right before the closing `</body>` tag at the bottom of your code. Additionally, replace "your-group-id" with your respective group ID. 
**Note: Do not wrap this in jQuery. Please make sure that this inline code so that the** `<script></script>` **tags are used. Do not put this JavaScript in another file as it may not work as intended.**
```
<script type="text/javascript">
     document.addEventListener("DOMContentLoaded", () => {
       console.log("DOM ready!");
  
       const iframe = document.getElementById("ddn-iframe");
  
       iframe.onload = function (e) {
         const frame = e.target;
         frame.contentWindow.postMessage({
           iframe: true,
           groupID: "YOUR-GROUP-ID",
           containerBgColor: "#fff"
         }, '*');
       }
  
       // Message Event Handler
       function resizeIframe(e) {
         if (e.origin !== window.location.origin) {
           iframe.height = e.data + "px";
         }
       }
  
       window.addEventListener("message", resizeIframe);
     });
</script>
```
