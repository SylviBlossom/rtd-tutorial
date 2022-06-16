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

Variables
^^^^^^^^^
- :data:`wave`
- :data:`attacker`
- :data:`damage`
- :data:`destroy_on_hit`
- :data:`remove_offscreen`
- :data:`tp`
- :data:`time_bonus`
- :data:`grazed`

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
- :func:`Bullet:init` (from :func:`Object:init`)
- :func:`Bullet:update` (from :func:`Object:update`)
- :func:`Bullet:draw` (from :func:`Object:draw`)