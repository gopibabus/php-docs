# Enums in OOPs

?> Added in v8.1

```php

// previously using a class
class Status {
  const DRAFT = 'Draft';
  const PUBLISHED = 'Published';
  const ARCHIVED = 'Archived';
}
// using an enum
enum PostStatus {
  case Draft;
  case Published;
  case Archived;
}
$status = PostStatus::Draft;

```