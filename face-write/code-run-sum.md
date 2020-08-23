```javascript
setTimeout(() => console.log(1));

  new Promise((res, rej) => {
    console.log(2);
    res(3)
  }).then(val => console.log(val))
  
  console.log(4)
  // 2 4 3 1
  
  
  
        async function async1() {
          console.log(1);
          const result = await async2();
          console.log(3);
        }
      
        async function async2() {
          console.log(2);
        }
      
        Promise.resolve().then(() => {
          console.log(4);
          return new Promise((resolve) => {
            console.log(7);
            setTimeout(() => {
              console.log(8);
              resolve();
            })
          }).then(() => {
            console.log(9);
          })
        });
      
        setTimeout(() => {
          console.log(5);
        });
      
        async1();
        console.log(6);
        
        // 1 2 6 4 7 3 5 8 9 
        
        
        
        async function async1() {
          console.log(1);
          const result = await async2();
          console.log(3);
        }
      
        async function async2() {
          console.log(2);
        }
              
        async1();

        Promise.resolve().then(() => {
          console.log(4);
        });
      
        setTimeout(() => {
          console.log(5);
        });
      
        console.log(6);
        
        // 1 2 6 3 4 5
    
    
    
     {
        let a = 1;
        var b = 2;
      }
      console.log(a);   // ReferenceError: a is not defined.
      console.log(b);   // 2 
      
      for (let i = 0; i < 10; i++) {
        // ...
      }
      console.log(i);  // ReferenceError: i is not defined
      
      for (let i = 0; i < 10; i++) {
        // ...
      }
      console.log(i); // 10
      
      
      
       var name = 'id';
        function fn() {
          console.log(name);
          var name = 'jd.hk';
          console.log(name);
        }
        fn();
        console.log(name)
        
        
        
        var name  = 'World!';
          (function() {
            if(typeof name === 'undefined'){
              var name = 'jack';
              console.log('Goodbye' + name);
            }else{
              console.log('Hello' + name)
            }
          })()
          // Goodbyejack
```
