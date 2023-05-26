# MINECRUFT
tak
from ursina import *
from ursina.prefabs.first_person_controller import FirstPersonController

app = Ursina()
player = FirstPersonController()
Sky()

boxes = []
for i in range(20):
    for j in range(20):
        box = Button(
            color=color.white,
            model='cube',
            position=(j, 0, i),
            texture='grass.png',
            parent=scene,
            origin_y=0.5
        )
        boxes.append(box)


class Animal(Entity):
    def __init__(self, position, texture):
        super().__init__(
            model='cube',
            scale=(1, 1, 1),
            texture=texture,
            collider='box',
            position=position
        )


def input(key):
    for box in boxes:
        if box.hovered:
            if key == 'left mouse down':
                new = Button(
                    color=color.white,
                    model='cube',
                    position=box.position + mouse.normal,
                    texture='grass.png',
                    parent=scene,
                    origin_y=0.5
                )
                boxes.append(new)
            if key == 'right mouse down':
                boxes.remove(box)
                destroy(box)


animals = []

animal_pig_1 = Animal(position=(5, 1, 5), texture='pngwing.com.png')
animals.append(animal_pig_1)

animal_duck2 = Animal(position=(10, 1, 10), texture='pngduck.com.png')
animals.append(animal_duck2)

animal_wolf_3 = Animal(position=(15, 1, 15), texture='pngwolf.com.png')
animals.append(animal_wolf_3)

app.run()
