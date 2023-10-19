```php
<?php

use PHPUnit\Framework\TestCase;
require __DIR__ . '/../src/Queue.php';


class QueueTest extends TestCase
{

    protected $queue;
// setup funkcija koja se izvrsava pre pocetka bilo kog testa
    public function setUp(): void
    {
        $this->queue = new Queue();
    }
// svaka funkcija za testiranje pocinje recju `test`
// alternativa je doc block sa *test* recju 
/**

@test
// u ovom slucaju nemora sadrzati rec test u nazivu funkcije
**/
    public function testNewQueueIsEmpty()
    {

        $this->assertEquals(0, $this->queue->getCount());

    }

    public function testAnItemIsAddedToQueue()
    {

        $this->queue->push('green');

        $this->assertEquals(1, $this->queue->getCount());

    }

    public function testIsItemRemovedFromQueue()
    {
        $this->queue->pop();

        $this->assertEquals(0, $this->queue->getCount());

    }

    public function testAnItemIsRemovedFromTheFrontOFTheQueue()
    {
        $this->queue->push('first');
        $this->queue->push('second');

        $this->assertEquals('first', $this->queue->pop());
    }
}
```