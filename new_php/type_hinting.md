# Type Hinting

## What is Type Hinting?

Declaring methods return type in the function definition is called **Type Hinting**.

Provides hints about input parameters type and return type.

```php
<?php

declare(strict_types=1);

class Students
{
    public function getList(): array
    {
        return [
            'gopi',
            'ammu',
            'lavanya',
            'dattu',
            'harika'
        ];
    }
}

class University
{

    private string $name = 'QIS';

    private array $students;

    public function __construct(Students $students)
    {
        $this->students = $students->getList();
    }

    public function getName(): string
    {
        return $this->name;
    }

    public function setName(string $name): void
    {
        $this->name = $name;
    }

    public function getStudents(): array {
        return $this->students;
    }
}

$students = new Students();
$university1 = new University($students);
$university1->getStudents();
```