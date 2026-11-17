# Game Development Notes (transcription)

Auto-transcribed from `Game dev.pdf` (OCR + AI correction). Diagrams/tables are approximate.

## Page 1
### Game Dev
#### Engine
```text
Date:
Game Dev
fahad.shafique@isb.nu.edu.pk
205F
\admin
Mar@c$labs
Course | %
25%
Ass
Proj
15%
S1
15
S2
15
F
20
Class
part
5
Quizzes
5
Game Dev & Dev
Scripts
Skeleton
3DC
2D
Game logic
Flow teams
scene management
Story line
UI/UX
platform integeration
Animation
home
VFX
physics engine
problem solving
Engine (what game made on)
R -> scaling
E -> rotation
[openGL] - low level
W -> position
Q -> moving
3Dmodels
design
L Blender, Maya 3D
press V -> join 2 things
L Shader (property of surface)
The Ball Game
Local Pos -> from parent
```

## Page 2
### Unity Editor Basics
#### Terrain Features
#### Camera Properties
```text
Unity Editor Basics
->Hierarchy: List all obj in scene
->Inspector: Shows properties of selected object
-> Scene view: where you arrange your game world
->project window: files
->Game view: what player sees
Date:
Gameobj: every thing in unity is gameobj
you can attach components to gameobj
1) Late update
updates every
FPS
eg Transform:
Mesh Renderer:
2) Fixupdate
Rigid body: physics, gravity
0.02 seconds - important as doesnt disrupt
physics
Script: custom behavior
3) update
Normally FPS
Script
public: inspector Visible
private:
Scenes: L your game environment
Prefab: = reusable gameobject template (eg bullet)
Terrain Features
left click    right click
Physics
Rigidbody: Gravity
paint textures: Apply different textures
L collider
(eg grass, rock, sand)
Smooth height: Avg out terrain height
for smoothness
Paint trees
UI basics  L canvas - container for UI
& details: place 3D trees
Text, button, image
Camera Properties
types of lights
directional: SUN, one direction
culling mask: include/exclude layers of object
spot lt: flashlight
clear flags: what to display on clear area (Skybox)
point light: like Bulb (all direction)
Projections: Perspective (obj get smaller with distance) or Orthographic ( no perspective)
area:
shader: scripts with calculations to calculate color of each pixel
Cam Depth: Render order of multiple cameras.
meshes: defines shape of obj
material: surface of obj references textures, color...
Viewport Rect: coordinates of where camera outputs on screen
Clipping Planes: Distances where rendering stops (near & far)
texture: bitmap images used by material to add detail
```

## Page 3
### Basic Scripting
#### Event Functions
#### Activate GameObject
```text
Date:
Basic Scripting
MonoBehaviour - base class
Awake = setup  Start = start gameplay
public class CheckState : MonoBehaviour
{
Event Functions
before start function after prefab instantiates
Awake: called when prefab instantiated, initial setup, runs even if Gameobj disabled
Start: called before first frame update, if script enabled, used for gameplay initialization
called after
Awake
Update: called once per frame, for regular input, logic, non physics
public class AwakeStart : MonoBehaviour
e.g
void Awake(){
Debug.log ("Awake called"
void start(){
FixedUpdate: called after fixed time step, physics calculation, called frequently
LateUpdate(): runs after update();
Activate Gameobject
SetActive: used to make 0
Active self: check if active
enabled
mono
void start(){
gameObject.SetActive (false);
}
```

## Page 4
#### Get Component
```text
Date:
public class ... : monob {
public GameObject myobject;
void start(){
Debug.Log ("Active self" + myObject.activeSelf);
}
.enabled = make obj enable/disable at runtime, for specific components eg mylight.enabled
gameobject.enabled
Get Component
Unity every Gameobj is a component
e.g Transform: position, rotation, scale
Rigidbody: physics gravity
meshRender: make visible
e.g
public class
MonoBehaviour {
Rigidbody rb;
// variable to hold Rigidbody
void start(){
// grab and attach component to variable
rb = Get Component < Rigidbody>();
void update(){
rb.AddForce ( Vector3.forward -5f);
GetComponent < meshRenderer >().enabled = false //hide object
```

## Page 5
#### Transform
#### Destroy
#### Input system
#### Instantiate
```text
vector3(x,y,z)
Date:
Transform
public float movespeed = 10f;
public float turnspeed = 50f;
void Update(){
if ( Input.GetKey (Keycode.UpArrow))
transform.Translate (Vector3.back * movespeed * Time.deltaTime);
if ( . . . . . . . down)
Time
( - vector.forward)
if (
current & Last
b/w
leftArrow)
Frame
frame rate independent
( Vector3.up, -turn...)
Destroy
Destroy (gameobject);
enemy
or GetComponent<meshRenderer>();
Input system
GetKeyUp
Input.GetButton
Instantiate: clone
playerInstance = Instantiate (gameobject, transform.position, rotation )
```

## Page 6
#### Prefabs
#### AudioSource
```text
Date:
Prefabs
Loop
is Playing
Pause
PlayOneShot
AudioSource.play
public class ... : Mono {
public AudioSource a1;
void start(){
a1.Play();
}
.PlayOneShot - played once
public AudioSource a1;
public AudioClip click sound;
void update{
if (input.GetKeyDown (KeyCode P))
a1.PlayOneShot (click sound)
```

## Page 7
### 2D Game Scripts
```text
Date:
Q1) Write script for 2D game - A, D for left right movement
- constant movement speed
- rotate on x axis
Q2)
coins collect they disappear
Ans1
class PlayerMovement : MonoBehaviour {
public float speed = 5f;
Rigidbody2D rb;
rb = getcomponent <Rigidbody2D>();
float move = 0f;
if ( input.GetKey(KeyCode.D)) move = 1f;
transform.Translate (Vector3.right * move * speed * Time.Delta)
transform.localScale = new vector3( 1,1,1)
(-1, 1, 1) flip on x axis
Ans2
public class CoinCollector : Mono {
private int score = 0;
void OnTriggerEnter2D(
if ( other.CompareTag ("Coin") ) {
Score++;
Debug.log ("Score:"+ Score);
Destroy (other.gameObject)
```

## Page 8
### Raycasting
```text
Date:
S2
1) Raycasting
detect object in direction you are pointing at 'ray' in shooting etc
void update(){
if (input.GetMouseButtonDown(0)){
Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition)
RaycastHit hit;
if ( Physics.Raycast( ray, out hit, 100f)){
print(hit)
}
if( Physics.Raycast (firePoint.position, firepoint.forward, out hit, range)
types
raycast
raycastAll
L returns all objects in line
RaycastHit[] hits = Physics.RaycastAll(.....)
spherecast
A thick ray
```

## Page 9
### Object Pooling
```text
movement
Transform.Translate (
movespeed * Time.Delta)
Date:
2) Object Pooling
Instead of using Instantiate(); Destroy();, again (lag)
we create objects once, store in list, reuse them activate/deactivate
item
Q)
Gun shoots 10 bullets per second.
step1) Variable
prefab = object to reuse
void update(){
poolsize
if (input.GetKeyDown(KeyCode.Space))
public class ObjectPool : MonoBehaviour{
bulletPool.GetFromPool( position, transform)
public GameObject prefab;
public int poolSize = 20;
public List <GameObject> pool = new List <GameObject>(); //make list of pool
pool list
void start(){
for( poolSize ){
GameObject obj = instantiate ( prefab); //instantiate
obj.setActive (false); //set inactive
pool.Add(obj);
void Get_Inactive_from_Pool( Vector3 position, Quaternion rotation){
foreach( obj in pool){
if( !obj.activeInHierarchy){
obj.transform.position
rotation
//reactivate
obj.setActive ( true);
return obj;
}void update(){
```

## Page 10
### Coroutine
```text
Date:
Coroutine
L function to pause/unpause game
void start(){
myRoutine
respawn enemy
IEnumerator RespawnEnemy(){
// conditions false before Delay
enemy.setActive (false);
yield return new WaitForSeconds(3f);
enemy.setActive (true); // resume operations after
Delay.
Note: You must call StartCoroutine(); each time before Func call
void onDeath()
enemy.setActive ( false
StartCoroutine ( RespawnEnemy());
```

## Page 11
### EnemyAI
```text
Date:
enemyAI
Scripts makes enemy
1. walk b/w two points (patrol)
2. Stop for a second.
3. Stop/Death animation when killed
NavMeshAgent: makes enemy move on walkable surface
Animator: animations
Waypoints: empty Gameobj; defines where enemy goes
using System.Collections; // IEnumerator for coroutines
using UnityEngine.AI; // NavMeshAgent for pathfinding
public class EnemyAI : MonoBehaviour{
public Animator animator;
Transform[] waypoints;
int currentwaypoint;
NavMeshAgent agent;
bool iswaiting, canmov;
void Start(){
currentwaypoint = 0, canmov = True
agent = GetComponent <NavMeshAgent>();
animator = Get com
agent.SetDestination ( waypoints [current way].position); // tells enemy to move to first waypoint
if (!canmov) return; //stops everything if cant move
Patrol();
}
void Patrol(){
if(!iswaiting && agent.RemainDistance < agent.stoppingDistance) //if enemy reached
destination wait
StartCoroutine (WaitandMoveToNextPoint(1f)); // 1 second
}
```

## Page 12
```text
Date:
IEnumerator WaitandMoveToNextPoint (float waittime){
iswaiting, agent.isstopped = true
animator.SetBool ('walk', false);
yield return new WaitSeconds (waitTime); // pause 1 second
currentwaypoint = (currentwaypoint +1) % waypoints.Length; // reverse
waypoint
agent.SetDestination ( waypoints [currentway].position)
animator.SetBool ("walk", true)
agent.isstopped = false, iswaiting = false
}
void Death (){
animator.SetBool ("walk", false)
agent.isstopped = true;
animator.SetTrigger ("Death")
}
Key syntax
NavMeshAgent   GetComponent <NavMeshAgent>();
agent.SetDestination //move enemy
agent.remainingDistance, agent.stoppingDistance, agent.isStopped
GetComp, .SetBool ('walk', false), SetTrigger ('walk',
Animator
Transform[]
+1 % length for loops, you pass it in the set destination
waypoints;
of agent
Array of points in scene
yield return new WaitSeconds ( time);
Coroutine/IEnumerator
```

## Page 13
### Enemy Health
```text
Date:
enemy Health
L external
public class enemyHealth : Mono {
int currentHealth
public image HealthProgressBar
void start(){
current health = maxhealth
}
void DecreaseHealth(){
current - amount;
updateHealthbar();
void updateHealthbar(){
HealthProgressBar.fillamount = current/totalhealth
if (currentH <0){
GetComponent < enemyAI>().Death(); // you can call another script
function
}
public image Healthbar
Healthbar
Healthbar.fillamount = int(current/total)
Death
GetComp< enemyAI>() Death();
```

## Page 14
### GUN
```text
Date:
GUN
using System.Collections;
using UnityEngine;
public class Gun : mono {
public GameObject gunCamera; // camera attached to gun
float range = 1000f;
ParticleSystem muzzleflash;
Audiosource audiosource;
AudioClip shootsound;
void Update(){
if ( Input.GetButtonDown("Fire1")) Shoot();
}
void Shoot(){
StartCoroutine ( FlashDelay(0.1f);) // 0.1sec muzzle flash delay
audiosource.PlayOneShot (shootsound);
RaycastHit hit;
if ( Physics.Raycast(gunCamera.transform.position, guncamera.
transform.forward, out hit, range)){
var hitobject = hit.transform.gameobject; //get obj that was hit
hitobject.getcomponent <enemyhealth>().DecreaseHealth();
}
GameObject.Instantiate (bulletimpact, hit.point, quaternion.LookRotation
}
void IEnumerator FlashDelay(time)
muzzleflash.play()
yield return
```

## Page 15
### Key syntax
### CPU / GPU Optimization
```text
Date:
Key syntax
obj.transform.forward
Raycasting =>  physics Raycast hit;
if (physics.raycast ( origin, direction, out hit, range))
obj.transform.position
guncamera
Coroutine =>
Instantiate
Gameobj.Instantiate ( prefab, position, rotation )
Quaternion.look Rotation
bullet
hit.point
impact
audio =>
AudioSource audiosource;
AudioSource.PlayOneShot ("sound")
particle system
Use NonAlloc Raycasts when multiple hits
Play();
Load order: Awake -> Start()
Stop();
CPU Optimization
Avoid heavy Awake/Start
CPU Optimization
scene load time
* CPU  L logic, physics, input
Delay expensive logic until after first frame
code optimization
avoid or Find Gameobj
minimize GetComponent
use coroutine instead of Update checks
GPU
L textures, shading, lights, particles
reduce draw calls made to GPU
Batching: Combine multiple obj to
GPU optim
dynamic batching
Texture optim: lower resolution, compress
LOD: level of detail
Baked lighting: precompute lighting & store use
```

## Page 16
### Vector3 and Transform
### PlayerMove
```text
Vector3
transform.position = new Vector3(0,5,0)
.lerp
vectors
int
vector3 result = lerp (src, dst, speed)
.localPosition =
rotation = new vector3 (...)
. MoveTowards (src, dst, units)
. Down, up, Left ....
(move towards target)
.scale:
Date:
change position to 0,5,0
using UnityEngine.SceneManagement;
SceneManager.LoadScene ( sceneName);
class PlayerMovement : Mono {
float movementspeed, jumpspeed
Rigidbody body
animator
LayerMask isGroundedLayer groundlayer
gameobj respawnpoint;
void Start(){
body = GetCom
animator = GetCo
boxcollider = GetC
}
void update(){
if (!canmove) return
horizontalInput = Input.GetAxis ("Horizontal") //if A/D
body.velocity = new vector2 (horizontalInput * movespeed, body.velocity.y)
if( Input.GetKeyDown (keycode.space)){ jump();}
if( horizontalInput >0){ // if right move, face right
transform.localScale = new Vector3(1,1,1) //
} same for left
animator.SetBool ("walk", true)
public bool isgrounded(){
Vector2.down
RaycastHit2D raycast = Physics2D.BoxCast ( boxcollider.bounds, size, 0, Vector2.down,
0.1f, groundlayer); isGrounded = raycasthit.collider
```

## Page 17
```text
```
