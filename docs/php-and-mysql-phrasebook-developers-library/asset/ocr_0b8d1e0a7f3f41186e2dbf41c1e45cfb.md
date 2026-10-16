can resolve these naming conflicts with the instanceof operator. Suppose, for example, that there are two traits, MyTrait1 and MyTrait2, both defining the showTime() method. The following syntax would make sure that no error occurs and that the showTime() implementation from MyTrait1 is used and not the one from MyTrait2:

```
class MyTraitClass {
    use MyTrait1, MyTrait2{
        MyTrait1::showTime insteadof MyTrait2;
    }
}
```

Another feature is the use of an alias, using the as keyword, or even the use of abstract methods within the trait. The following code listing uses two traits, insteadof, and an alias, and returns an output similar to the one in Figure 4.3:

```
<?php
    trait MyTrait1 {
        public function showTime() {
            $date = new DateTime('now');
            echo $date->format('H:i:s');
        }

        public function showCopyright() {
            echo '&copy; Trait 1';
        }
    }

    trait MyTrait2 {
        public function showCopyright() {
            echo '&copy; Trait 2';
        }
    }
```