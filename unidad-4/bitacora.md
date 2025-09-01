# Evidencias para la unidad 4

## Código

Código para ofApp.h:

``` cpp
#pragma once
#include "ofMain.h"

// Nodo de la cola
struct Node {
	float x, y;
	float radius;
	ofColor color;
	float opacity;
	Node * next;

	Node(float _x, float _y, float _radius, ofColor _color, float _opacity)
		: x(_x)
		, y(_y)
		, radius(_radius)
		, color(_color)
		, opacity(_opacity)
		, next(nullptr) {
	}
};

// Implementación manual de una cola (FIFO)
class BrushQueue {
public:
	Node * front;
	Node * rear;
	int size;
	int maxSize;

	BrushQueue(int _maxSize);
	~BrushQueue();

	void enqueue(float x, float y, float radius, ofColor color, float opacity);
	void dequeue();
	void clear();
	bool isEmpty();
};

// Constructor
BrushQueue::BrushQueue(int _maxSize)
	: front(nullptr)
	, rear(nullptr)
	, size(0)
	, maxSize(_maxSize) { }

// Destructor
BrushQueue::~BrushQueue() {
	clear();
}

// Implementa aquí `enqueue()`
void BrushQueue::enqueue(float x, float y, float radius, ofColor color, float opacity) {

	Node * firstNode = new Node(x,y, radius, color, opacity);

	if (rear == nullptr) {
		front = rear = firstNode;
	} else {
		rear->next = firstNode;
		rear = firstNode;
	}

	if (size == maxSize) {
		dequeue();
	}
	else
	{
		size++;
	}


	// TODO: crear un nuevo nodo y agregarlo al final de la cola.
	// Si la cola supera `maxSize`, eliminar el nodo más antiguo con `dequeue()`.
}

// Implementa aquí `dequeue()`
void BrushQueue::dequeue() {

	if (front == nullptr) {
		return; 
	}

	Node * oldestNode = front; 
	front = front->next; 
	if (front == nullptr) {
		rear = nullptr;
		size = 0;
	}
	delete oldestNode;
	// TODO: eliminar el nodo más antiguo si la cola no está vacía.
}

// Implementa aquí `clear()`
void BrushQueue::clear() {
	// TODO: eliminar todos los nodos de la cola.
	Node * current = front; //no importa por donde empiece, más facíl desde el principio.
	while (current != nullptr) {
		Node * nextNode = current->next;
		delete current;
		current = nextNode;
	}
	front = rear = nullptr;
	size = 0;
}

// Implementa aquí `isEmpty()`
bool BrushQueue::isEmpty() {

	if (front == nullptr) {
		return true; 
	}
	else {
		return false; 
	}
	// TODO: retornar si la cola está vacía.
}

class ofApp : public ofBaseApp {
public:
	BrushQueue strokes; // Cola de trazos
	float backgroundHue = 0;

	float colorHue = 128;

	ofApp()
		: strokes(50) { } // Tamaño máximo de la cola

	void setup();
	void update();
	void draw();
	void keyPressed(int key);
};


```

Código para ofApp.cpp:

``` cpp
#include "ofApp.h"

int opacity = 0;

//--------------------------------------------------------------
void ofApp::setup() {
	ofBackground(0);
}

//--------------------------------------------------------------
void ofApp::update() {
	backgroundHue += 0.2;
	colorHue += 0.5;

	if (backgroundHue > 255) backgroundHue = 0;
	if (colorHue > 255) colorHue = 0;


	if (ofGetMousePressed() == true) {

		strokes.enqueue(ofGetMouseX(), ofGetMouseY(), ofRandom(10, 30), ofColor::fromHsb(colorHue, 200, 255), 0); // ni idea pq se pone blanco
	}
	// TODO: agregar un nuevo trazo si el mouse está presionado.
	// Usa strokes.enqueue(x, y, radius, color, opacity);
}

//--------------------------------------------------------------
void ofApp::draw() {
	// Fondo con gradiente dinámico
	ofColor color1, color2;
	color1.setHsb(backgroundHue, 150, 240);
	color2.setHsb(fmod(backgroundHue + 50, 255), 150, 240);
	ofBackgroundGradient(color1, color2, OF_GRADIENT_CIRCULAR);


	Node * current = strokes.front;

	if (strokes.front == nullptr)
	{
		return; 
	}

    int index = 0;

    while (current)
	{
		current->opacity = index * (255 / strokes.maxSize);
		ofSetColor(current->color, current->opacity);
		ofDrawCircle(current->x, current->y, current->radius);
		current = current->next;
		index++;
    }

	
}

	// TODO: dibujar los trazos almacenados en la cola.
	// Recorre los nodos desde strokes.front hasta nullptr y usa ofDrawCircle().

//--------------------------------------------------------------
void ofApp::keyPressed(int key) {
	if (key == 'c') {
		strokes.clear();
	}
	if (key == 'a') {
		if (strokes.maxSize == 50)
		{
			strokes.clear();
			strokes.maxSize = 100;
		}
		else if (strokes.maxSize == 100)
		{
			strokes.clear();
			strokes.maxSize = 50;
		}
	} else if (key == 's') {
		ofSaveFrame();
	}
}


```

Código para main.cpp:
``` cpp
#include "ofMain.h"
#include "ofApp.h"

//========================================================================
int main( ){

	//Use ofGLFWWindowSettings for more options like multi-monitor fullscreen
	ofGLWindowSettings settings;
	settings.setSize(1024, 768);
	settings.windowMode = OF_WINDOW; //can also be OF_FULLSCREEN

	auto window = ofCreateWindow(settings);

	ofRunApp(window, std::make_shared<ofApp>());
	ofRunMainLoop();

}
```

## Demostración:

[Aquí está el video demostrativo de mi aplicación](https://youtu.be/5KZmqily77w)

