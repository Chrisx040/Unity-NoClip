
<h1>Unity NoClip</h1>


<h3>siga os passos:</h3>
<li>escolha um jogo unity</li>
<li>pegue a libil2cpp.so e a globalmetadata.dat</li>





</br></br></br></br>





<pre> <code>// é importante usar incluir essa biblioteca no projeto.

#include &lt;cmath&gt;

bool NoClip = false;
  
void (*get_radius)(void *instance, float radius);

void (old_Player)(void *instance);
void Player(void *instance) {
   if (instance != NULL) {
    if (NoClip) {
    set_radius(instance,INFINITY);
    }
   }
  old_Player(instance);
}

MSHookFunction((void *) getAbsoluteAddress("libil2cpp.so", 0x00000, (void *) &Player, (void **) &old_Player); //instância do jogador   

  

  
</code>

  
</pre>




