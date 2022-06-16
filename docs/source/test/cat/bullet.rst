Bullet
======
(*extends* :doc:`Object </index>`)

Overview
--------

Bullets are the most important part of any attack, and as such, they can be
complicated to set up. This section will first explain creating generic bullets
without making new files for them, then detail how to extend them.

.. note::

    By default, all bullets have a scale of 2, and an origin of 0.5, 0.5. This means
    its collider, sprite, and any other children will be relative to the topleft
    of the bullet's ``width`` and ``height``, which are automatically set to the dimensions
    of its sprite if the bullet is initiated with a path specified (in other words,
    making all children relative to the topleft of the bullet's sprite). When making
    any bullet's collider, remember that it will be scaled 2x because of this.

Class Members
-------------
(*see* :doc:`Object </index>` *for inherited members*)

.. attributetable:: 

Variables
^^^^^^^^^
- :attr:`wave <Bullet.wave>`
- :attr:`attacker <Bullet.attacker>`
- :attr:`damage <Bullet.damage>`
- :attr:`destroy_on_hit <Bullet.destroy_on_hit>`
- :attr:`remove_offscreen <Bullet.remove_offscreen>`
- :attr:`tp <Bullet.tp>`
- :attr:`time_bonus <Bullet.time_bonus>`
- :attr:`grazed <Bullet.grazed>`

Useful Functions
^^^^^^^^^^^^^^^^
- :func:`Bullet:setSprite(texture, [speed, loop, on_finished]) <Bullet.setSprite>`
- :func:`Bullet:isBullet(id) <Bullet.isBullet>`

Overridable Functions
^^^^^^^^^^^^^^^^^^^^^
- :func:`Bullet:getTarget() <Bullet.getTarget>`
- :func:`Bullet:getDamage() <Bullet.getDamage>`
- :func:`Bullet:onDamage(soul) <Bullet.onDamage>`
- :func:`Bullet:onCollide(soul) <Bullet.onCollide>`
- :func:`Bullet:onWaveSpawn(wave) <Bullet.onWaveSpawn>`

Internal / Class Overrides
^^^^^^^^^^^^^^^^^^^^^^^^^^
- ``Bullet:update()`` (from :func:`Object:update() <Object.update>`)
- ``Bullet:draw()``   (from :func:`Object:draw() <Object.draw>`)

Class Reference
------------------
.. class:: Bullet(x, y, texture)

    Creates a new instance of the Bullet class.

    :param numbers x,y: The position of the bullet.
    :param string texture: The path to the bullet's texture.

    .. method:: setSprite(texture, [speed, loop, on_finished])

        Sets the sprite of the bullet to the specified path, and changes the bullet's ``width`` and ``height`` variables to the dimensions of the sprite. ``speed``, ``loop``, and ``on_finished`` will be passed into the sprite's ``play()`` function.

        :param string texture: The path to the bullet's texture.
        :param speed: The animation delay between frames.
        :type speed: number, optional
        :param loop: Whether the animation should loop.
        :type loop: boolean, optional
        :param on_finished: A function to call when the animation finishes.
        :type on_finished: function, optional

    .. attribute:: wave

        A reference to the current Wave class that is active. Gets defined after ``init()``, but only if spawned through :func:`Wave:spawnBullet`; otherwise, it is never defined.

        :type: Wave

    .. attribute:: attacker

        A reference to the enemy associated with the bullet. Gets defined after ``init()``, but only if spawned through :func:`Wave:spawnBullet`; otherwise, it is never defined.

        :type: EnemyBattler

    .. attribute:: damage

        Amount of damage the bullet does. If not provided, the game will calculate damage based on the enemy's attack.

        :type: number

    .. attribute:: destroy_on_hit

        Whether the bullet will be removed when it collides with the player. ``true`` by default.

        :type: boolean

    .. attribute:: remove_offscreen

        Whether the bullet will be removed when it goes offscreen. ``true`` by default.

        :type: boolean

    .. attribute:: tp

        The amount of TP (in percentage) the player gains from grazing the bullet. Defaults to 1.6 (1/10th of a defend).

        :type: number

    .. attribute:: time_bonus

        The number of frames, based on 30fps, that the wave's length will be reduced by when grazing the bullet. Apparently this is a mechanic in Deltarune.

        :type: number

    .. attribute:: grazed

        *(Internal)* Whether the bullet has already been grazed. (reduces graze rewards)

        :type: boolean