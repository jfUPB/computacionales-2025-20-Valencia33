# Bitácora de aprendizaje de la unidad 5

## 1. 🐸 **Diagnóstico inicial** 🐸

___

## 🐟 Actividad 01 🐟

### 🪸 **Parte 1: recordando los conceptos (en C#)** 🪸

1.) ¿Qué es el encapsulamiento para ti?

- Como evitar el acceso a metodos o atributos por medio de public, private, protected y el otro que no me acuerdo. Esto sirve para que algunos atributos o métodos solo puedan ser accedidos por la clase que los contiene.

2.) ¿Qué es la herencia?

- La herencia es utilizada para el polimorfismo, esta permite que una clase tenga subclases que **heredan** sus atributos y métodos, de esta forma es mucho más facil implementar clases derivadas.

3.) ¿Qué es el polimorfismo?

- Creo que el polimorfismo hace referencia a la reutilización de métodos, es decir, darle diferentes usos a un solo metodo utilizando abstract y override para sobreescribir el método y darle diferentes comportamientos.

### 🪸 **Parte 2: análisis de código (en C#)** 🪸

1.) Señala una línea de código que sea un ejemplo claro de encapsulamiento

**Encapsulamiento**

> private string nombre;

- Es un ejemplo de encapsulamiento puesto que utiliza la palabra reservada private, y de esta forma solo puede ser accesible por la clase que la contiene, es por eso que tiene un método accesor (?) este permite realizar un chequeo de la variable y así evitar que se le de un valor inadecuado.

2.) ¿Por qué crees que el campo nombre es private pero la propiedad Nombre es public? ¿Qué problema se evita con esto?

- No sabía que esta era la siguiente pregunta. Pero basicamente ese método que está en public normalmente se utilizar para proteger el atributo "real" que es el que está privado, es un metodo que puede leer y cambiar ese atributo privado pero además puede  definir unas reglas por las cuales decide si le cambia o no el valor a ese atributo, de esa forma evita que el atributo privado cambie su valor a algo inadecuado.

**Herencia**

1.) ¿Cómo se evidencia la herencia en la clase Circulo?
  
  - Se evidencia en dos instancias; La primera siendo su constructor, donde hereda el nombre de figura y ya viene definido como "Círculo". La otra sería cuando implementa el método Dibujar(), este lo hereda de *Figura* sin embargo se le indica que lo debe sobreescribir y añadir un comportamiento propio de el.

2.) Un objeto de tipo Circulo, además de Radio, ¿Qué otros datos almacena en su interior gracias a la herencia?

- El método del que hablé y el nombre.

**Polimorfismo**

1.) Observa el bucle foreach.  ¿Cómo crees que funciona esto “por debajo”?

No tengo la menor idea. Pero me imagino que por medio de los punteros que componen la lista este foreach pasa por cada uno ejecutando el método indicado, pero realmente hasta ahí me llega la imaginación. Se que esto se hace en el heap puesto que la lista y los objetos que tiene son variables dinámicas pero más allá de eso pienso que si es recorriendo la lista, chequeando que el objeto en el que va si es una figura y por último ejecutando el método correspondiente.

### 🪸 **Parte 3: hipótesis sobre la implementación** 🪸 

1.) Cuando creas un objeto Rectangulo, este tiene Base, Altura y también Nombre. ¿Cómo te imaginas que se organizan esos tres datos en la memoria del computador para formar un solo objeto?

- Me imagino que cuando se crea se refiere a instanciar el objeto, por lo que creo que esa instancia de Rectangulo crea copias de esos 3 atributos a los cuales, como objeto, está apuntando, y esos punteros son los que junto al objeto se guardan en el Heap. Sin embargo, creo que para el caso del Nombre es diferente puesto que este tiene que primero crear una copia del atributo de quien hereda, más no de el mismo. Realmente no tengo ni idea pero si pienso que un objeto está guardado en el heap y está compuesto por copias de atributos de la clase a la que pertenece.

2.) Pensemos de nuevo en la llamada fig.Dibujar(). El compilador solo sabe que fig es una Figura. ¿Cómo decide el programa, mientras se está ejecutando, si debe llamar al Dibujar del Circulo o al del Rectangulo?

- Creo que es como lo dije más temprano, el foreach recorre la lista por medio de los punteros, entonces cuando llega a un objeto que es una Figura este no lo observa como algo tan general puesto que tiene acceso al objeto específico por medio de los punteros, de esta forma, ese momento *fig* es realmente ese objeto. De esa forma el programa sabe que método llamar.

3.) ¿Cómo crees que el compilador logra que no puedas acceder a un miembro private desde fuera de la clase? ¿Es algo que se revisa cuando escribes el código, o es una protección que existe mientras el programa se ejecuta?

- No tengo ni idea. Diría que tambien es por medio de punteros, y me refiero a que si se intenta acceder a ese atributo por medio de un puntero que no sale de la clase entonces este no podrá ser accedido, y diría que el filtro se hace por medio de los objetos, que permiten acceder a esos punteros. Y pienso eso por que es lo único que se me ocurre, definitivamente es algo con los punteros, pero como realmente funcione no sé.

### 🪸 **Parte 4: y tu autoevaluación y primeras preguntas** 🪸

- Voy a definir una pregunta pero igual me voy a ir por la ruta guiada esperando que eventualmente me respondan a mi pregunta.

1.) ¿Como funciona la manipulación de la memoria en C++ cuando se implementan los conceptos de herencia, encapsulamiento y polimorfismo?

___

## 🐟 Actividad 02 🐟

## 2. 🐸 **La pregunta inicial** 🐸

- ***¿Como funciona la manipulación de la memoria en C++ cuando se implementan los conceptos de herencia, encapsulamiento y polimorfismo?***

### 3.  **Registro de exploración:** 

> Aquí documentas cada ciclo de pregunta -> hipótesis -> experimento -> hallazgo -> reflexión.
> Debe ser rico en evidencia visual (código, capturas del depurador con anotaciones, diagramas).

- **Analiza el código de la aplicación y trata de explicar en tus propias palabras qué está haciendo**

El código cada frame está chequeando por 3 inputs, click izquierdo, espacio y la s, el más interesante de estos tres es el click izquierdo puesto que este llama el método createRisingParticle() el cual se encarga de "calcular" todos los parámetros necesitados para crear una particula de este tipo y de esa forma, al final del método, llamar el método constructor de la particula para pasarle esos parámetros.

Este tipo de particula hereda gran parte de sus carácteristicas de una clase base llamada Particula, la cual solamente declara varios métodos en virtual para que sean o no sobreescritos, de estos los más interesantes son los métodos de update() y draw(). El primero se encarga de modificar la edad y posición de la particula a medida que pasa el tiempo. Adicionalmente este también se encarga de definir cuando debería explotar la particula, definiendo si se encuentra en una zona llamda explosionThreshold.

<img width="781" height="306" alt="image" src="https://github.com/user-attachments/assets/12b78e35-4e3e-474c-8607-8eb2cacf1166" />

Volviendo a ofApp.cpp observamos que en el método update() se hace un chequeo del frame anterior en cada frame ahí se evalua por cada particula si esta debería de explotar, llamando al metodo shouldExplode() de cada una, si este devuelve true entonces genera un número random entre 0 y 2 para definir que tipo de explosión va a realizar.

<a name="exp1"></a>
Experimento 1:

<img width="941" height="538" alt="image" src="https://github.com/user-attachments/assets/d8464400-3410-459a-992b-d563cbf062d6" />

Estos tipos de explosiones son objetos que heredan de una clase base llamada ExplosionParticle la cual hereda de Particle. 

Los tipos de particula son los siguientes CircularExplosion, RandomExplosion y StarExplosión, todas tres se diferencian en que forma y con que patrón evolucionan las particulas.

Ya por último se limpia la memoria chequeando si en el frame anterior esa particula estaba muerta.

___

## 🐟 Actividad 03 🐟

- 🧐🧪✍️ **Antes de ejecutar el experimento, ¿Qué esperas ver en memoria (hipótesis)? Ejecuta el código y muestra una captura de pantalla del objeto en la memoria. ¿Qué puedes observar? ¿Qué información te proporciona el depurador? ¿Qué puedes concluir?**

  - Previo a ejecutar el programa espero ver en el depurador una variable llamada como esa clase que va a tener "instancias" de los métodos que menciona, realmente no estoy seguro.

<img width="920" height="316" alt="image" src="https://github.com/user-attachments/assets/d47b681e-ccfe-46a5-8cd1-ecaf992a0170" />

Observo que ofApp está compuesto por una herencia a ofBaseApp donde observamos que viene con dos variables MouseX y MouseY, además, por fuera de esta herencia observamos que tiene un atributo llamado particles el cual es un vector que está compuesto por punteros a cada particula.

-  🧐🧪✍️ **Trata de buscar en memoria todas las partes que componen al objeto tipo CircularExplosion ¿Qué puedes observar en la memoria? ¿Qué información te proporciona el depurador? ¿Qué puedes concluir?**

<img width="1208" height="513" alt="image" src="https://github.com/user-attachments/assets/a7b6f276-3100-4c27-b851-ee1e1e8866a4" />

<img width="1210" height="471" alt="image" src="https://github.com/user-attachments/assets/647094a8-bb94-4bac-8da0-bb1f027f22d4" />

<img width="1201" height="468" alt="image" src="https://github.com/user-attachments/assets/fa5b2db1-127b-4ca0-a5c5-f3d171b67b26" />

Observo como CircularExplosion está compuesto completamente por herencias; hereda primero de ExplosionParticle y con esa viene Particle, observo los atributos por los cuales está compuesto el objeto y concluyo que pa crear un objeto de estos hay que hacer mil cosas, y que sacar un random es la tarea más dura de un computador. Aparte de esto concluyo que un objeto el cual tiene herencias recibe con el toda la clase que hereda, y va con todos sus atributos.

- 🧐🧪✍️ **Captura la _vtable de un objeto CircularExplosion, pega la imagen en tu bitácora, pero observa detenidamente la tabla de funciones. ¿Qué puedes observar?**



## 4.  **Consolidación, autoevaluación y cierre:**
> [!CAUTION]
> Esta sección es OBLIGATORIA y central para tu evaluación

## Apply: Aplicación 🛠

### Particulas Nuevas

Para las particulas que hay crear lo primero que hice fue implementar un switch dentro de createRisingParticle() el cual se encarga de definir que particula se va a crear.

**WiggleParticle**

Esta particula cambia su comportamiento aumentando su velocidad, además, su posición en x es modificada de tal forma que "baile". En un principio pensé que la función cos() me ayudaría sumandole a la posición para que bailara un poco. Esto no funcionó entonces decidí crear dos variables dinámicas las cuales se encargan de modificar el valor de xOffset para que de esa forma si baile. No se me ocurre otra forma más simple de implementarlo.

Esto tampoco funcionó entonces volví a intentarle a la trigonometría, la cual fue mucho más fácil de implementar despues de leer sobre la función seno, básicamente Asen(Bx+BC), donde A es la amplitud, B el periodo y C el desfase horizontal, pero ese no lo usé.

```
class WiggleParticle : public Particle {
protected:
	glm::vec2 position;
	glm::vec2 velocity;
	ofColor color;
	float lifetime; // tiempo máximo antes de explotar
	float age;
	bool exploded;

public:
	WiggleParticle(const glm::vec2 & pos, const glm::vec2 & vel, const ofColor & col, float life)
		: position(pos)
		, velocity(vel)
		, color(col)
		, lifetime(life)
		, age(0)
		, exploded(false) {
	}

	void update(float dt) override {
		position.y += velocity.y * dt;
		age += dt;
		// Aumenta la desaceleración para dar sensación de recorrido largo
		velocity.y += 9.8f * dt / 8;

		position.x += sin(age * 10) * 150 * dt ;

		// Condición de explosión: cuando la partícula alcanza aproximadamente el 15% de la altura
		float explosionThreshold = ofGetHeight() * 0.15 + ofRandom(-30, 30);
		if (position.y <= explosionThreshold || age >= lifetime) {
			exploded = true;
		}
	}

	void draw() override {

		color.setHsb(age/lifetime * 255, 255, 255);

		ofSetColor(color);
		// Partícula más grande
		ofDrawRectangle(position, 10, 10);
	}

	bool isDead() const override { return exploded; }
	bool shouldExplode() const override { return exploded; }
	glm::vec2 getPosition() const override { return position; }
	ofColor getColor() const override { return color; }
};
```

**ResizeParticle**

Tengo la idea de hacer una particula que deje como una estela, pero sé que eso de alguna forma tiene algo que ver con un array y me da miedo.

Aunque primero voy a hacer que incremente su tamaño a medida que sube y que cambie su color pq es más fácil y no quiero tratar con un array.

Me rindo eso está muy duro.

Ya desde hace un tiempo conocía la siguiente función ofDrawRectRounded() la cual permite dibujar un rectangulo con esquinar redondeadas, por lo que en mi mente me deja cambiar de un circulo a un rectangulo, solo es cuestión de encontrar los extremos que pueda tomar ese valor. Por esto (y por que no sé inicializar un array) decidí hacer una particula que cambiara de tamaño y forma a medida que sube.

Para lograr este cambio utilicé la función ofClamp() que basicamente no deja que un valor se salga de un rango, entonces de esa forma es muy fácil mantener ese valor "normalizado" y fue el que utilicé para 

```
// -------------------------------------------------
// TrailParticle: Partícula que nace en la parte inferior y sube dejando una línea
// -------------------------------------------------

class TrailParticle : public Particle {
protected:
	glm::vec2 position;
	glm::vec2 velocity;
	ofColor color;
	float lifetime; // tiempo máximo antes de explotar
	float age;
	bool exploded;

public:
	TrailParticle(const glm::vec2 & pos, const glm::vec2 & vel, const ofColor & col, float life)
		: position(pos)
		, velocity(vel)
		, color(col)
		, lifetime(life)
		, age(0)
		, exploded(false) {
	}

	void update(float dt) override {
		position.y += velocity.y * dt;
		age += dt;
		position.x += sin(age * 10) * 150 * dt;
		velocity.y += 9.8f * dt / 8;

		// Condición de explosión: cuando la partícula alcanza aproximadamente el 15% de la altura
		float explosionThreshold = ofGetHeight() * 0.15 + ofRandom(-30, 30);
		if (position.y <= explosionThreshold || age >= lifetime) {
			exploded = true;
		}
	}

	void draw() override {

		float t = ofClamp(age / lifetime, 0, 1);
		float size = ofLerp(10, 40, t);

		color.setHsb(age / lifetime * 255, 255, 255);
		ofSetColor(color);
		float roundness = ofMap(t, 0, 0.5f, size, size / 4);
		ofDrawRectRounded(position.x - size / 2, position.y - size / 2, size, size, roundness);

	}

	bool isDead() const override { return exploded; }
	bool shouldExplode() const override { return exploded; }
	glm::vec2 getPosition() const override { return position; }
	ofColor getColor() const override { return color; }
};

```

### Explosión Rectangular.

<img width="699" height="401" alt="image" src="https://github.com/user-attachments/assets/b4396357-c83a-49d5-9430-33a03c10987a" />

En un principio decidí implementar esta clase de explosión, precisamente por que es muy simple y es casi que una copia exacta de la Explosión random, me sirvió como acercamiento a los conceptos de la unidad.

Sin embargo como ya dije, me pareció una implementación bastante simple, por lo que modifiqué sus parametros para que fuera mucho más interesante. Implemente un cambio de tamaño de las particulas, entonces ahora es más como una implosión y adicionalmente añadí un cambio de color para las particular.

Entonces la cambié para que fuera más interesante, y quedó así:

<img width="713" height="732" alt="image" src="https://github.com/user-attachments/assets/b9f85cc6-2fb7-4706-9101-8b2245130466" />

Aprendí de la existencia de ofPushMatrix() y ofPopMatrix() por que se me estaba dañando el canva con esas rotaciones, entonces empecé a modificarlo y terminé haciendo un tipo de explosión totalmente diferente:

```
class ThreeDimensionalExplosion : public ExplosionParticle {
public:

	float width;
	float height;
	float hue;
	float opacity;

	ThreeDimensionalExplosion(const glm::vec2 & pos, const ofColor & col)
		: ExplosionParticle(pos, glm::vec2(0, 0), col, 1.5f, ofRandom(16, 32)) {
		float angle = ofRandom(0, TWO_PI);
		float speed = ofRandom(80, 200);

		width = 50;
		height = 50;
		opacity = 100;
		hue = 0;

		velocity = glm::vec2(cos(angle), sin(angle)) * speed;
	}

	void draw() override {

		hue++;
		opacity--;

		color.setHsb(hue, 220, 255, opacity);
		ofSetColor(color);

		width -= 1;
		height -= 1;

		ofPushMatrix();
		ofTranslate(position.x, position.y);
		ofRotateDeg(hue*50, 0, 0, 1);
		ofDrawRectangle(-size / 2, -size / 2, size, size);
		ofPopMatrix();
	}
};
```
___
___

### App.cpp

```
#include "ofApp.h"

// --------------------------------------------------------------
void ofApp::setup() {
	ofSetFrameRate(60);
	ofBackground(0);
}

// --------------------------------------------------------------
void ofApp::update() {
	float dt = ofGetLastFrameTime();

	// Actualiza todas las partículas
	for (int i = 0; i < particles.size(); i++) {
		particles[i]->update(dt);
	}

	// Procesa las partículas (iteración en reversa para facilitar eliminación)
	for (int i = particles.size() - 1; i >= 0; i--) {
		// Si la partícula debe explotar, generamos nuevas explosiones
		if (particles[i]->shouldExplode()) {
			int explosionType = (int)ofRandom(4); // 0: Circular, 1: Random, 2: Star
			int numParticles = (int)ofRandom(20, 30);
			for (int j = 0; j < numParticles; j++) {
				if (explosionType == 0) {
					particles.push_back(new CircularExplosion(particles[i]->getPosition(), particles[i]->getColor()));
				} else if (explosionType == 1) {
					particles.push_back(new RandomExplosion(particles[i]->getPosition(), particles[i]->getColor()));
				} else if (explosionType == 2) {
					particles.push_back(new StarExplosion(particles[i]->getPosition(), particles[i]->getColor()));
				} else if (explosionType == 3) {
					particles.push_back(new ThreeDimensionalExplosion(particles[i]->getPosition(), particles[i]->getColor()));
				}
			}
			delete particles[i];
			particles.erase(particles.begin() + i);
		} else if (particles[i]->isDead()) {
			delete particles[i];
			particles.erase(particles.begin() + i);
		}
	}
}

// --------------------------------------------------------------
void ofApp::draw() {
	for (int i = 0; i < particles.size(); i++) {
		particles[i]->draw();
	}
}

// --------------------------------------------------------------
void ofApp::createParticle() {
	ofLog() << "hola soy createParticle, no sé de donde me llaman";
	// Genera una RisingParticle cerca del centro inferior (con variación horizontal)
	float minX = ofGetWidth() * 0.35;
	float maxX = ofGetWidth() * 0.65;
	float spawnX = ofRandom(minX, maxX);
	glm::vec2 pos(spawnX, ofGetHeight());
	// La partícula apunta hacia un objetivo en la parte superior central
	glm::vec2 target(ofGetWidth() / 2 + ofRandom(-300, 300), ofGetHeight() * 0.10 + ofRandom(-30, 30));
	glm::vec2 direction = glm::normalize(target - pos);
	// Velocidad ajustada para recorrer una mayor distancia
	glm::vec2 vel = direction * ofRandom(250, 350);
	ofColor col;
	col.setHsb(ofRandom(255), 220, 255);
	float lifetime = ofRandom(1.5, 3.5); // Tiempo de vida antes de explotar

	int particleType = (int)ofRandom(3);

	switch (particleType)
	{
	case 0:
		particles.push_back(new WiggleParticle(pos, vel, col, lifetime));
		break;
	case 1:
		particles.push_back(new TrailParticle(pos, vel, col, lifetime));
		break;
	case 2:
		particles.push_back(new RisingParticle(pos, vel, col, lifetime));
		break;
	}


}

// --------------------------------------------------------------
void ofApp::mousePressed(int x, int y, int button) {
	createParticle();
}

// --------------------------------------------------------------
void ofApp::keyPressed(int key) {
	if (key == ' ') {
		for (int i = 0; i < 1000; i++) {
			createParticle();
		}
	}
	if (key == 's') {
		ofSaveScreen("screenshot_" + ofToString(ofGetFrameNum()) + ".png");
	}
}

// --------------------------------------------------------------
ofApp::~ofApp() {
	for (int i = 0; i < particles.size(); i++) {
		delete particles[i];
	}
	particles.clear();
}
```

#OfApp.h

```
#pragma once
#include "ofMain.h"
#include <vector>

// -------------------------------------------------
// Clase base abstracta: Particle
// -------------------------------------------------
class Particle {
public:
	virtual ~Particle() { }
	virtual void update(float dt) = 0;
	virtual void draw() = 0;
	virtual bool isDead() const = 0;
	// Nuevo método para saber si la partícula (tipo RisingParticle) debe explotar
	virtual bool shouldExplode() const { return false; }
	// Métodos para obtener posición y color, para usarlos en explosiones
	virtual glm::vec2 getPosition() const { return glm::vec2(0, 0); }
	virtual ofColor getColor() const { return ofColor(255); }
};

// -------------------------------------------------
// RisingParticle: Partícula que nace en la parte inferior central y sube
// -------------------------------------------------
class RisingParticle : public Particle {
protected:
	glm::vec2 position;
	glm::vec2 velocity;
	ofColor color;
	float lifetime; // tiempo máximo antes de explotar
	float age;
	bool exploded;

public:
	RisingParticle(const glm::vec2 & pos, const glm::vec2 & vel, const ofColor & col, float life)
		: position(pos)
		, velocity(vel)
		, color(col)
		, lifetime(life)
		, age(0)
		, exploded(false) {
	}

	void update(float dt) override {
		position += velocity * dt;
		age += dt;
		// Aumenta la desaceleración para dar sensación de recorrido largo
		velocity.y += 9.8f * dt * 8;
		// Condición de explosión: cuando la partícula alcanza aproximadamente el 15% de la altura
		float explosionThreshold = ofGetHeight() * 0.15 + ofRandom(-30, 30);
		if (position.y <= explosionThreshold || age >= lifetime) {
			exploded = true;
		}
	}

	void draw() override {
		ofSetColor(color);
		// Partícula más grande
		ofDrawCircle(position, 10);
	}

	bool isDead() const override { return exploded; }
	bool shouldExplode() const override { return exploded; }
	glm::vec2 getPosition() const override { return position; }
	ofColor getColor() const override { return color; }
};

// -------------------------------------------------
// TrailParticle: Partícula que nace en la parte inferior y sube dejando una línea
// -------------------------------------------------

class TrailParticle : public Particle {
protected:
	glm::vec2 position;
	glm::vec2 velocity;
	ofColor color;
	float lifetime; // tiempo máximo antes de explotar
	float age;
	bool exploded;

public:
	TrailParticle(const glm::vec2 & pos, const glm::vec2 & vel, const ofColor & col, float life)
		: position(pos)
		, velocity(vel)
		, color(col)
		, lifetime(life)
		, age(0)
		, exploded(false) {
	}

	void update(float dt) override {
		position.y += velocity.y * dt;
		age += dt;
		position.x += sin(age * 10) * 150 * dt;
		velocity.y += 9.8f * dt / 8;

		// Condición de explosión: cuando la partícula alcanza aproximadamente el 15% de la altura
		float explosionThreshold = ofGetHeight() * 0.15 + ofRandom(-30, 30);
		if (position.y <= explosionThreshold || age >= lifetime) {
			exploded = true;
		}
	}

	void draw() override {

		float t = ofClamp(age / lifetime, 0, 1);
		float size = ofLerp(10, 40, t);

		color.setHsb(age / lifetime * 255, 255, 255);
		ofSetColor(color);
		float roundness = ofMap(t, 0, 0.5f, size, size / 4);
		ofDrawRectRounded(position.x - size / 2, position.y - size / 2, size, size, roundness);

	}

	bool isDead() const override { return exploded; }
	bool shouldExplode() const override { return exploded; }
	glm::vec2 getPosition() const override { return position; }
	ofColor getColor() const override { return color; }
};


// -------------------------------------------------
// WiggleParticle: Partícula que nace en la parte inferior y sube BAILANDO
// -------------------------------------------------

class WiggleParticle : public Particle {
protected:
	glm::vec2 position;
	glm::vec2 velocity;
	ofColor color;
	float lifetime; // tiempo máximo antes de explotar
	float age;
	bool exploded;

public:
	WiggleParticle(const glm::vec2 & pos, const glm::vec2 & vel, const ofColor & col, float life)
		: position(pos)
		, velocity(vel)
		, color(col)
		, lifetime(life)
		, age(0)
		, exploded(false) {
	}

	void update(float dt) override {
		position.y += velocity.y * dt;
		age += dt;
		// Aumenta la desaceleración para dar sensación de recorrido largo
		velocity.y += 9.8f * dt / 8;

		position.x += sin(age * 10) * 150 * dt ;

		// Condición de explosión: cuando la partícula alcanza aproximadamente el 15% de la altura
		float explosionThreshold = ofGetHeight() * 0.15 + ofRandom(-30, 30);
		if (position.y <= explosionThreshold || age >= lifetime) {
			exploded = true;
		}
	}

	void draw() override {

		color.setHsb(age/lifetime * 255, 255, 255);

		ofSetColor(color);
		// Partícula más grande
		ofDrawRectangle(position, 10, 10);
	}

	bool isDead() const override { return exploded; }
	bool shouldExplode() const override { return exploded; }
	glm::vec2 getPosition() const override { return position; }
	ofColor getColor() const override { return color; }
};


// -------------------------------------------------
// Clase base para explosiones: ExplosionParticle
// -------------------------------------------------
class ExplosionParticle : public Particle {
protected:
	glm::vec2 position;
	glm::vec2 velocity;
	ofColor color;
	float age;
	float lifetime;
	float size; // tamaño de la partícula de explosión
public:
	ExplosionParticle(const glm::vec2 & pos, const glm::vec2 & vel, const ofColor & col, float life, float sz)
		: position(pos)
		, velocity(vel)
		, color(col)
		, age(0)
		, lifetime(life)
		, size(sz) {
	}

	void update(float dt) override {
		position += velocity * dt;
		age += dt;
		float alpha = ofMap(age, 0, lifetime, 255, 0, true);
		color.a = alpha;
	}

	bool isDead() const override { return age >= lifetime; }
};

// -------------------------------------------------
// CircularExplosion: Explosión en patrón circular
// -------------------------------------------------
class CircularExplosion : public ExplosionParticle {
public:
	CircularExplosion(const glm::vec2 & pos, const ofColor & col)
		: ExplosionParticle(pos, glm::vec2(0, 0), col, 1.2f, ofRandom(16, 32)) {
		float angle = ofRandom(0, TWO_PI);
		float speed = ofRandom(80, 200);
		velocity = glm::vec2(cos(angle), sin(angle)) * speed;
	}

	void draw() override {
		ofSetColor(color);
		ofDrawCircle(position, size);
	}
};

// -------------------------------------------------
// RandomExplosion: Explosión con direcciones aleatorias
// -------------------------------------------------
class RandomExplosion : public ExplosionParticle {
public:
	RandomExplosion(const glm::vec2 & pos, const ofColor & col)
		: ExplosionParticle(pos, glm::vec2(0, 0), col, 1.5f, ofRandom(16, 32)) {
		velocity = glm::vec2(ofRandom(-200, 200), ofRandom(-200, 200));
	}

	void draw() override {
		ofSetColor(color);
		ofDrawRectangle(position.x, position.y, size, size);
	}
};

// -------------------------------------------------
// StarExplosion: Explosión en forma de estrella
// -------------------------------------------------
class StarExplosion : public ExplosionParticle {
public:
	StarExplosion(const glm::vec2 & pos, const ofColor & col)
		: ExplosionParticle(pos, glm::vec2(0, 0), col, 1.3f, ofRandom(20, 40)) {
		float angle = ofRandom(0, TWO_PI);
		float speed = ofRandom(90, 180);
		velocity = glm::vec2(cos(angle), sin(angle)) * speed;
	}

	void draw() override {
		ofSetColor(color);
		int rays = 5;
		float outerRadius = size;
		float innerRadius = size * 0.5;
		ofPushMatrix();
		ofTranslate(position);
		for (int i = 0; i < rays; i++) {
			float theta = ofMap(i, 0, rays, 0, TWO_PI);
			float xOuter = cos(theta) * outerRadius;
			float yOuter = sin(theta) * outerRadius;
			float xInner = cos(theta + PI / rays) * innerRadius;
			float yInner = sin(theta + PI / rays) * innerRadius;
			ofDrawLine(0, 0, xOuter, yOuter);
			ofDrawLine(xOuter, yOuter, xInner, yInner);
		}
		ofPopMatrix();
	}
};

// -------------------------------------------------
// 3DExplosion: Explosión rectangular 3D
// -------------------------------------------------
class ThreeDimensionalExplosion : public ExplosionParticle {
public:

	float width;
	float height;
	float hue;
	float opacity;

	ThreeDimensionalExplosion(const glm::vec2 & pos, const ofColor & col)
		: ExplosionParticle(pos, glm::vec2(0, 0), col, 1.5f, ofRandom(16, 32)) {
		float angle = ofRandom(0, TWO_PI);
		float speed = ofRandom(80, 200);

		width = 50;
		height = 50;
		opacity = 100;
		hue = 0;

		velocity = glm::vec2(cos(angle), sin(angle)) * speed;
	}

	void draw() override {

		hue++;
		opacity--;

		color.setHsb(hue, 220, 255, opacity);
		ofSetColor(color);

		width -= 1;
		height -= 1;

		ofPushMatrix();
		ofTranslate(position.x, position.y);
		ofRotateDeg(hue*50, 0, 0, 1);
		ofDrawRectangle(-size / 2, -size / 2, size, size);
		ofPopMatrix();
	}
};

// -------------------------------------------------
// ofApp: Manejo de la escena y eventos
// -------------------------------------------------
class ofApp : public ofBaseApp {
public:
	void setup();
	void update();
	void draw();
	void mousePressed(int x, int y, int button);
	void keyPressed(int key);

	std::vector<Particle *> particles;
	~ofApp();

private:
	void createParticle();
};

```


- **¿Cómo y por qué de la implementación de cada una de las extensiones solicitadas al caso de estudio?**

	-   La implementación de las particulas fue hecha siguiendo este proceso que empieza con una pregunta ¿que quiero que haga la particula? Desde un principio ya sabía que quería mantener el comportamiento de subir como un fuego pirotécnico por lo que ese comportamiento lo deje. En el caso de WiggleParticle quería replicar el movimiento que tienen algunos fuegos pirotécnicos que suben como haciendo oscilaciones, además quería que su color retrara que tan cerca estaba de explotar. Implementar este en particular me llamó la atención precisamente por que fue mu fácil gracias a la herencia y polimorfismo que había entre todas estas clases, lo mismo para el caso de las explosiones, donde solamente fue modificar comportamientos particulares pero no sobreescribir la clase por completo.

  	-  Por otra parte para TrailParticle (a la cual me niego cambiarle el nombre) quise en un principio que dejara como una estela a medida que subía, esto no me funcionó entonces me rendí y pasé a usar otra función que ya me llamaba la atención desde hace un rato que es la de ofDrawRectRounded()  entonces pensé que sería genial que su tamaño cambiara a medida que subía, como de cierta forma dar un indicio de que va a explotar, entonces creé una nueva variable por que si lo hacía con un tiempo predeterminado se dañaba y aprendí a usar ofClamp para lograr el resultado que quería. Al final se le dañan las esquinas pero voy a hacer como que ese era el resultado esperado.

- **¿Cómo y por qué de la implementación de los conceptos de encapsulamiento, herencia y polimorfismo en tu código?**

	-  En el caso de las particulas estas tienen sus atributos con la palabra reservada protected, lo que impide que se puedan modificar fuera de la clase, la única forma en la que esto puede pasar es por medio de los métodos públicos de la clase, el por que de esto es precisamente para que el comportamiento de las particulas solamente puede ser accedido y modificado desde la clase a la que le pertene, lo único que depende de un agente externo sería su instanciación.
 	-  La herencia es evidenciada en las clases añadidas puesto que todas heredan de Particula sus atributos, comprendiendo tambien que es una clase abstracta y por lo tanto no se puede instanciar. Esto nos ahorra un montón de tiempo pues como dije antes hace que la tarea de implementar una nueva particula sea algo rápido.
  	-  Por último el polimorfismo es la base del funcionamiento de estas particulas, puesto que todas heredan de Particula unos metodos virtuales (draw() y update()) que cada una puede sobreescribir y añadir comportamientos propios de cada una. Encima tambien le quita trabajo de más al computador pues se llaman a través de punteros pues la lista de particles las guarda todas.

- **Explica cómo verificaste que cada una de las extensiones funciona correctamente, muestra capturas de pantalla del depurador donde evidencias lo anterior, en particular el polimorfismo en tiempo de ejecución.**

	-  Para verificar que cada una funcionaba correctamente modificaba el código de tal forma que solo fuera posible llamar aquella que estaba testeando, se me ocurrió otra forma que no fuera tan destructiva que sería añadir nuevos inputs para instanciar estas clases pero en últimas decidí que mejor no por que se me ocurrió una forma de implementarlas rápidamente con un switch. En últimas solo fue cambiar el valor que indica que clase se instancia. Me pasó algo curioso con el switch y es que olvidé el break; entonces instanciaba las tres particulas al mismo tiempo.

   <img width="737" height="472" alt="image" src="https://github.com/user-attachments/assets/63d2c68e-37a3-472b-946f-4ea97ef8c423" />

   <img width="914" height="506" alt="image" src="https://github.com/user-attachments/assets/8fcbc34a-e41a-47ee-9227-5798fb303053" />

    -  Verificación de que las extensiones funcionan correctamente y polimorfismo en tiempo de ejecución:

<img width="914" height="306" alt="image" src="https://github.com/user-attachments/assets/ddb6ed7b-98ce-4ac3-8a66-a0681e2f7bb4" />

<img width="926" height="173" alt="image" src="https://github.com/user-attachments/assets/640e5045-8683-4b58-be70-16e7bbd5f752" />

Se observa como el computador realmente ve WiggleParticle como una Particula, pero tiene punteros que apuntan a los métodos propios de esta Particula, acá se evidencia claramente el polimorfismo.

## Consolidación, autoevaluación y cierre

- 1.) **Mi nota propuesta: 4.5**

- 2.) **Justificación general:**

	- Pienso que mi investigación fue extensa cuando había conceptos que no entendía o que me generaban curiosidad, esto puede ser evidenciado en las activadades de set/seek y principalmente en la de apply en la cual me causó mucha curiosidad el ver como existía en la memoria la instancia de una clase que yo había creado. Aparte de esto siento que la actividad de apply me brindó un espacio para realizar experimentos no solo con respecto a la memoria pero tambien utilizando la documentación de OF para lograr lo que tenía en mente. Esto me permitía no solo comprender sino aplicar los conceptos que vimos en esta unidad.

- 3.) **Mapeo de evidencias según la rúbrica:**

	- **Criterio 1: profundidad de la indagación**

   		- Mi autoevaluación: 5/5
     	-  A medida que avanzaba en la unidad me di cuenta que mi pregunta inicial evolucionó no solo para entender el como se implementa el encapsulamiento, polimorfismo y herencia en la memoria sino también para entender el por qué de la implementación de estos de esa forma, el caso que creo tiene más peso es el del polimorfismo, en el cual me llamó mucho la atención como los métodos son realmente llamados con punteros propios de Particula, me dió lugar a entender con mayor profundidad estos conceptos.
    
	- **Criterio 2: esfuerzo cognitivo y experimentación**

   		- Mi autoevaluación 4/5
     	- A pesar de que no realicé muchos experimentos por fuera de lo que propuso el profe siento que respondí todas las preguntas y dudas que me surgieron teniendo en cuenta el enfoqué que di con mi pregunta y fue cambiando a medida que la pregunta iba evolucionando, por lo que por el lado del esfuerxo cognitivo siento que lo hice bastante bien, más allá de esto siento que a pesar de que no alteré los experimentos que propuso el profe si los analicé y entendí, lo que me dió herramientas para seguir cambiando y mejorando mis preguntas. Por ejemplo, el [experimento1](#exp1)
    
	- **Criterio 3: calidad del análisis y la reflexión**

   		- Mi autoevaluación: 5/5
     	- Siento que mi punto fuerte en esta unidad fue 100% la implementación de las nuevas clases en el Apply, lo menciono por que siento que no hubo mejor forma de demostrar que si había comprendido los conceptos de polimorfismo, encapsulamiento y herencia que logrando hacer esa implementación desde cero, teniendo en cuenta la naturaleza de las clases que ya habían sido creadas y tales. Aparte de esto siento que para el código del Apply demostré interés en aprender y profundizar más en lo que podía ofrecer openframeworks, e incluso si en algunas partes me estancaba con el uso de algunos elementos esto solamente me daba la excusa de seguir intentando con otros aspectos o experimentos en el Apply.
  
	- **Criterio 4: apropiación y articulación de conceptos**

  		- Mi autoevaluación: 4/5
    	- A pesar de que siento que mi apropiación con los conceptos fue buena y completa realmente no hice ningún esfuerzo por intentar plasmarlo de una forma articulada en la bitacora, realmente escribir acá no es mi punto fuerte por eso pienso que en este criterio falté un poco cuando se trata de las evidencias en la bitacora, por esto pero tambien por mi correcta apropiación de los conceptos pienso que es justo esta nota. 
