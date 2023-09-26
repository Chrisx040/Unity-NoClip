
<h1>Unity NoClip</h1>


<h3>siga os passos:</h3>
<li>escolha um jogo unity</li>
<li>pegue a libil2cpp.so e a globalmetadata.dat</li>
<li>despeja-a e entre no arquivo</li>



</br>

<p>o jogo que usarei como exemplo será o <strong>blockstrike</strong> (versão antiga)</p>

<p>primeiro passo devemos encontrar a classe do nosso jogador.</p>

<p>no meu caso é a classe <strong>PlayerInput</strong></p>

<p>irei usar o metódo Update() para nosso gancho C++</p>

<p>agora devemos procurar um field que se refere a classe CharacterController ou uma classe que se refere a CharacterController </br>na classe do meu jogador tem o field que aponta para a classe <strong>CharacterController</p>




<code>public CharacterController mCharacterController; // 0x8C</code>
 </br>

<p>após isso ja podemos fazer nossa função em C++</p>

<pre><code>#include &lt;cmath&gt;

void (*set_radius)(void *instance, float radius);

void (*_Player)(void *instance);
void Player(void *instance) {
    if (instance != NULL) {
      void *CharacterController = *(void**)((uin64_t)instance + 0x8C);
      if (CharacterController != NULL) {
        set_radius(CharacterController,INFINITY)
      }
    }
    _Player(instance)
}


MSHookFunction((void *) getAbsoluteAddress("libil2cpp.so", 0x00000), (void *) &Player, (void **) &_Player); // PlayerInput | update();  

set_radius = (void(*)(void*,float))getAbsoluteAddress("libil2cpp.so", 0x000000) //CharacterController | set_radius(float value);
</code>
</pre>






