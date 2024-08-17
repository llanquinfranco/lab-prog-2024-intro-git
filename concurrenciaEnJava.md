# Semaforos en Java

    Un tipo simple de semáforo es el binario, que puede tomar solamente los valores 0 y 1.
    Se inicializan en 1 y son usados cuando sólo un proceso puede acceder a un recurso a la vez. Se les 
suele llamar mutex.

Los semáforos pueden ser usados para diferentes propósitos, entre ellos:
    Implementar cierres de exclusión mutua o locks.
    Barreras.
    Permitir a un máximo de N hilos acceder a un recurso, inicializando el semáforo en N.
    Notificación. Inicializando el semáforo en 0 puede usarse para comunicación entre threads
sobre la disponibilidad de un recurso

Puedes crear un semáforo especificando el número de permisos que quieres que tenga. 
Por ejemplo, para crear un semáforo con un único permiso (similar a un bloqueo mutuo), puedes
hacer lo siguiente:
Semaphore semaphore = new Semaphore(1);

También puedes crear un semáforo con múltiples permisos, especificando un número mayor:
Semaphore semaphore = new Semaphore(3);

Sus metodos principales son:
acquire(): Este método se utiliza para adquirir un permiso del semáforo. Si no hay permisos 
disponibles, el hilo que llama a este método se bloqueará hasta que un permiso esté disponible.

try {
    semaphore.acquire();
} catch (InterruptedException e) {
    Thread.currentThread().interrupt();
}

release(): Este método se utiliza para liberar un permiso, devolviéndolo al semáforo. Esto permite
que otros hilos puedan adquirir el permiso.
semaphore.release();

tryAcquire(): Este método intenta adquirir un permiso si está disponible en el momento de la 
llamada, y devuelve true si tiene éxito, o false si no hay permisos disponibles. No bloquea el 
hilo.
boolean acquired = semaphore.tryAcquire();

availablePermits(): Este método devuelve el número actual de permisos disponibles en el semáforo.
int available = semaphore.availablePermits();
