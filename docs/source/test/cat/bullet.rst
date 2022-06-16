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
- :attr:`wave`
- :attr:`attacker`
- :attr:`damage`
- :attr:`destroy_on_hit`
- :attr:`remove_offscreen`
- :attr:`tp`
- :attr:`time_bonus`
- :attr:`grazed`

Useful Functions
^^^^^^^^^^^^^^^^
- :func:`Bullet:setSprite`
- :func:`Bullet:isBullet`

Overridable Functions
^^^^^^^^^^^^^^^^^^^^^
- :func:`Bullet:getTarget`
- :func:`Bullet:getDamage`
- :func:`Bullet:onDamage`
- :func:`Bullet:onCollide`
- :func:`Bullet:onWaveSpawn`

Internal / Class Overrides
^^^^^^^^^^^^^^^^^^^^^^^^^^
- :func:`Bullet:update` (from :func:`Object:update`)
- :func:`Bullet:draw`   (from :func:`Object:draw`)

Class Reference
------------------
.. class:: Bullet(x, y, texture)

    Creates a new instance of the Bullet class.

    :param numbers x,y: The position of the bullet.
    :param string texture: The path to the bullet's texture.

    .. attr:: wave
        A reference to the current Wave class that is active. Gets defined after ``init()``, but only if spawned through :func:`Wave:spawnBullet`; otherwise, it is never defined.

        :type: Wave

    .. attr:: attacker
        A reference to the enemy associated with the bullet. Gets defined after ``init()``, but only if spawned through :func:`Wave:spawnBullet`; otherwise, it is never defined.

        :type: EnemyBattler
    
    .. attr:: damage
        Amount of damage the bullet does. If not provided, the game will calculate damage based on the enemy's attack.

        :type: number
    
    .. attr:: destroy_on_hit
        Whether the bullet will be removed when it collides with the player. ``true`` by default.

        :type: boolean
    
    .. attr:: remove_offscreen
        Whether the bullet will be removed when it goes offscreen. ``true`` by default.

        :type: boolean

    .. attr:: tp
        The amount of TP (in percentage) the player gains from grazing the bullet. Defaults to 1.6 (1/10th of a defend).

        :type: number

    .. attr:: time_bonus
        The number of frames, based on 30fps, that the wave's length will be reduced by when grazing the bullet. Apparently this is a mechanic in Deltarune.

        :type: number

    .. attr:: grazed
        *(Internal)* Whether the bullet has already been grazed. (reduces graze rewards)

        :type: boolean

.. function:: Bullet:setSprite(texture, [speed, loop, on_finished])
    Sets the sprite of the bullet to the specified path, and changes the bullet's ``width`` and ``height`` variables to the dimensions of the sprite. ``speed``, ``loop``, and ``on_finished`` will be passed into the sprite's ``play()`` function.

    :param string texture: The path to the bullet's texture.
    :param speed: The animation delay between frames.
    :type speed: number, optional
    :param loop: Whether the animation should loop.
    :type loop: boolean, optional
    :param on_finished: A function to call when the animation finishes.
    :type on_finished: function, optional