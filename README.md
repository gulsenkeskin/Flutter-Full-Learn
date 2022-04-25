# Notlar

*Mixin class* 

Bir sınıfa özellikler ekleme: mixins

Mixins, bir sınıfın kodunu birden çok sınıf hiyerarşisinde yeniden kullanmanın bir yoludur.

Bir mixin kullanmak için with anahtar sözcüğünü ve ardından bir veya daha fazla mixin adını kullanın. Aşağıdaki örnek, mixins kullanan iki sınıfı göstermektedir:

```
class Musician extends Performer with Musical {
  // ···
}

class Maestro extends Person with Musical, Aggressive, Demented {
  Maestro(String maestroName) {
    name = maestroName;
    canConduct = true;
  }
}
```

Bir mixin uygulamak için, Object'i genişleten ve hiçbir constructor bildirmeyen bir sınıf oluşturun. Mixin'inizin normal bir sınıf olarak kullanılmasını istemiyorsanız, class yerine mixin anahtar sözcüğünü kullanın. Örneğin:

```
mixin Musical {
  bool canPlayPiano = false;
  bool canCompose = false;
  bool canConduct = false;

  void entertainMe() {
    if (canPlayPiano) {
      print('Playing piano');
    } else if (canConduct) {
      print('Waving hands');
    } else {
      print('Humming to self');
    }
  }
}

```

bazen mixin, mixin 'in tanımlandığı bir methodu çağırabilmeye bağlı olabilir. Aşağıdaki örnekte gösterildiği gibi, gerekli üst sınıfı belirtmek için on anahtar sözcüğünü kullanarak bir mixin kullanımını kısıtlayabilirsiniz:

```
class Musician {
  // ...
}
mixin MusicalPerformer on Musician {
  // ...
}
class SingerDancer extends Musician with MusicalPerformer {
  // ...
}
```

Önceki kodda, yalnızca Musician sınıfını extend veya implement eden sınıflar Mixin MusicalPerformer'ı kullanabilir. SingerDancer, Musician'ı extend ettiği için SingerDancer, MusicalPerformer'da mix yapabilir.

kaynak: https://dart.dev/guides/language/language-tour#adding-features-to-a-class-mixins



