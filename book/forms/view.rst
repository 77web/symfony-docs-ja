.. index::
   pair: Forms; View

�e���v���[�g���Ńt�H�[�����g�p����
==================

Symfony2�� :doc:`�t�H�[�� </book/forms/overview>` �̓t�B�[���h�łł��Ă��܂��B�t�B�[���h�̓t�H�[���̈Ӗ����L�q���Ă���A�G���h���[�U�ɑ΂���\�����L�q���Ă���킯�ł͂���܂���B����́A�t�H�[����HTML�Ɋ֘A�t����K�v���Ȃ����Ƃ��Ӗ����Ă��܂��B����ɁA���ꂼ��̃t�H�[���t�B�[���h���v�����Ƃ���ɕ\������邱�Ƃ́A�E�F�u�f�U�C�i�[�̐ӔC�ɂȂ�Ƃ������Ƃł��B�������ASymfony2��PHP�����̃w���p�[��Twig�e���v���[�g��񋟂��邱�ƂŁA�t�H�[���̓����ƃJ�X�^�}�C�Y���ȒP�ɂ��Ă��܂��B

�t�H�[�����u�蓮�Łv�\������
----------------------------

Symfony2�̃��b�p�[�����Symfony2���ǂ̂悤�ɊȒP�ɂ��m���ł��΂₭�t�H�[���̕\�����ł���悤�菕������̂��ɂ��ďڂ������Ă����O�ɁA�����Ȃ��Ƃ���ł͉������ʂȂ��Ƃ��N���Ă���킯�ł͂Ȃ��Ƃ������Ƃ�m���Ă����K�v������܂��BSymfony2�̃t�H�[����\�������邽�߁A�ǂ��HTML���g�����Ƃ��ł���̂ł��B

.. code-block:: html

    <form action="#" method="post">
        <input type="text" name="name" />

        <input type="submit" />
    </form>

�o���f�[�V�����̃G���[������ꍇ�A�������΂₭�C�����邽�߁A�G���[��\�����A�t�B�[���h�ɑ��M���ꂽ�l������ׂ��ł��傤�B����ɂ̓t�H�[����p�̃��\�b�h���g�������ł��B

.. configuration-block::

    .. code-block:: html+jinja

        <form action="#" method="post">
            <ul>
                {% for error in form.name.errors %}
                    <li>{{ error.0 }}</li>
                {% endfor %}
            </ul>
            <input type="text" name="name" value="{{ form.name.data }}" />

            <input type="submit" />
        </form>

    .. code-block:: html+php

        <form action="#" method="post">
            <ul>
                <?php foreach ($form['name']->getErrors() as $error): ?>
                    <li><?php echo $error[0] ?></li>
                <?php endforeach; ?>
            </ul>
            <input type="text" name="name" value="<?php $form['name']->getData() ?>" />

            <input type="submit" />
        </form>

Symfony2�̃w���p�[�́A�e���v���[�g��Z��������A�t�H�[���̃��C�A�E�g���ȒP�ɃJ�X�^�}�C�Y�ł���悤�ɂ�����A���ۉ����T�|�[�g������ACSRF����������A�t�@�C�����A�b�v���[�h�ł�����Ƃ��������Ƃ��ȒP�ɂł��Ă��܂��܂��B�ȍ~�̃Z�N�V�����ŁA�����ɂ��Đ������Ă����܂��B

�t�H�[����\������
-----------------

�t�H�[���̃O���[�o���ȍ\��(�t�H�[���^�O�⑗�M�{�^���Ȃ�)�̓t�H�[���C���X�^���X�Œ�`����Ă���킯�ł͂Ȃ��̂ŁA�g������HTML�R�[�h�����R�Ɏg�����Ƃ��ł��܂��B�P���ȃt�H�[���̃e���v���[�g�͈ȉ��̂悤�ɓǂݍ��݂܂��B

.. code-block:: html

    <form action="#" method="post">
        <!-- Display the form fields -->

        <input type="submit" />
    </form>

�O���[�o���ȃt�H�[���̍\���ȊO�ɂ��A�O���[�o���ȃG���[��B���t�B�[���h��\�����邽�߂̕��@���K�v�ł��BSymfony2�͂��̖������ʂ����w���p�[��p�ӂ��Ă��܂��BTwig�e���v���[�g�ɂ����Ă����̃w���p�[�́A�t�H�[����t�H�[���̃t�B�[���h�ɓK�p�ł���O���[�o���Ȋ֐��Ƃ��Ď�������Ă��܂��BPHP�e���v���[�g�ɂ����Ắu�t�H�[���v�w���p�[���A�t�H�[����t�H�[���̃t�B�[���h���p�����[�^�Ƃ��Ď󂯓����p�u���b�N���\�b�h��ʂ��ē����@�\��񋟂��Ă��܂��B

.. configuration-block::

    .. code-block:: html+jinja

        <form action="#" method="post">
            {{ form_errors(form) }}

            <!-- �t�H�[���̃t�B�[���h��\������ -->

            {{ form_hidden(form) }}
            <input type="submit" />
        </form>

    .. code-block:: html+php

        <form action="#" method="post">
            <?php echo $view['form']->errors($form) ?>

            <!-- �t�H�[���̃t�B�[���h��\������ -->

            <?php echo $view['form']->hidden($form) ?>

            <input type="submit" />
        </form>

.. note::

    ���Ă̒ʂ�ATwig�̊֐��́uform\_ �v�Ŏn�܂�܂��B�u�t�H�[���v�w���p�[�̃��\�b�h�ƈقȂ�A�����̊֐��̓O���[�o���Ȃ̂ŁA���O���d�����₷���̂Œ��ӂ��Ă��������B

.. tip::

    �f�t�H���g�ł́A ``errors`` �w���p�[�� ``<ul>`` ���X�g�𐶐����܂��B����́A���̃h�L�������g�̌�ɏo�Ă���悤�ɁA�ȒP�ɃJ�X�^�}�C�Y���邱�Ƃ��ł��܂�

Last but not the least, a form containing a file input must contain the
``enctype`` attribute; use the ``enctype`` helper to take render it:
�Ō�ɏd�v�Ȃ��ƂƂ��āA�t�@�C�����͂��܂ރt�H�[���� ``enctype`` ���������K�v������܂��B���̂悤�ȃt�H�[���������_�����O����ۂ� ``enctype`` �w���p�[���g�p���܂��傤�B

.. configuration-block::

    .. code-block:: html+jinja

        <form action="#" {{ form_enctype(form) }} method="post">

    .. code-block:: html+php

        <form action="#" <?php echo $view['form']->enctype($form) ?> method="post">

�t�B�[���h��\������
-----------------

�t�H�[���̃t�B�[���h�ւ̃A�N�Z�X�́ASymfony2�̃t�H�[�����z��Ƃ��ē��삷��̂Ɠ������炢�ȒP�ł��B

.. configuration-block::

    .. code-block:: html+jinja

        {{ form.title }}

        {# �O���[�v user ���ɓ���q�ɂȂ����t�B�[���h first_name �ɃA�N�Z�X #}
        {{ form.user.first_name }}

    .. code-block:: html+php

        <?php $form['title'] ?>

        <!-- �O���[�v user ���ɓ���q�ɂȂ����t�B�[���h first_name �ɃA�N�Z�X -->
        <?php $form['user']['first_name'] ?>

���ꂼ��̃t�B�[���h��Field�C���X�^���X�ł��邱�Ƃ���A��Ɏ������悤�ɕ\�����邱�Ƃ͂ł��܂���B�w���p�[�����Ɏg�p���Ă��������B

``render`` �w���p�[�́A�t�B�[���h��HTML�\���������_�����O���܂��B

.. configuration-block::

    .. code-block:: jinja

        {{ form_field(form.title) }}

    .. code-block:: html+php

        <?php echo $view['form']->render($form['title']) ?>

.. note::

    �t�B�[���h�̃e���v���[�g�́A��Ŋw�K����悤�Ƀt�B�[���h�̃N���X�������ɂ��đI������Ă��܂��B

``label`` �w���p�[�́A�t�B�[���h�Ɋ֘A�t����ꂽ ``<label>`` �^�O�������_�����O���܂��B

.. configuration-block::

    .. code-block:: jinja

        {{ form_label(form.title) }}

    .. code-block:: html+php

        <?php echo $view['form']->label($form['title']) ?>

�f�t�H���g�ł́ASymfony2�̓t�B�[���h�����u�l�Ԃ��ǂ߂�悤�Ɂv���܂����A�Ǝ��̃��x�������邱�Ƃ��ł��܂��B

.. configuration-block::

    .. code-block:: jinja

        {{ form_label(form.title, 'Give me a title') }}

    .. code-block:: html+php

        <?php echo $view['form']->label($form['title'], 'Give me a title') ?>

.. note::

    Symfony2�͎����I�ɑS�Ẵ��x���ƃG���[���b�Z�[�W�����ۉ����܂��B

``errors`` �w���p�[�̓t�B�[���h�̃G���[�������_�����O���܂��B

.. configuration-block::

    .. code-block:: jinja

        {{ form_errors(form.title) }}

    .. code-block:: html+php

        <?php echo $view['form']->errors($form['title']) ?>

HTML�̕\�����`����
--------------------------------

�w���p�[��HTML�������_�����O���邽�߂ɁA�e���v���[�g�Ɉˑ����Ă��܂��B�f�t�H���g��Symfony2�́A�S�Ẵr���g�C���t�B�[���h�ɑ΂��ăe���v���[�g���֘A�t�����Ă��܂��B

Twig�e���v���[�g�ł́A���ꂼ��̃w���p�[��1�̃e���v���[�g�u���b�N�Ɋ֘A�t�����Ă��܂��B�Ⴆ�� ``form_errors`` �֐���  ``errors`` �u���b�N�Ɋ֘A�Â��Ă��܂��B�r���g�C���t�B�[���h�͈ȉ��̂悤�ɏ�����Ă��܂��B

.. code-block:: html+jinja

    {# TwigBundle::form.html.twig #}

    {% block errors %}
        {% if errors %}
        <ul>
            {% for error in errors %}
                <li>{% trans error.0 with error.1 from validators %}</li>
            {% endfor %}
        </ul>
        {% endif %}
    {% endblock errors %}

PHP�e���v���[�g�ł͂���Ƃ͈قȂ�A���ꂼ��̃w���p�[��1��PHP�e���v���[�g�Ɋ֘A�Â��Ă��܂��B ``errors()`` �w���p�[�́A�ȉ��̂悤�� ``errors.php`` �e���v���[�g�Ɋ֘A�Â��܂��B

.. code-block:: html+php

    {# FrameworkBundle:Form:errors.php #}

    <?php if ($errors): ?>
        <ul>
            <?php foreach ($errors as $error): ?>
                <li><?php echo $view['translator']->trans($error[0], $error[1], 'validators') ?></li>
            <?php endforeach; ?>
        </ul>
    <?php endif; ?>

�ȉ��̓w���p�[�Ƃ���Ɋ֘A�t����ꂽ�u���b�N��e���v���[�g�̈ꗗ�ł��B

========== ================== ==================
�w���p�[   Twig �u���b�N      PHP �e���v���[�g��
========== ================== ==================
``errors`` ``errors``         ``FrameworkBundle:Form:errors.php``
``hidden`` ``hidden``         ``FrameworkBundle:Form:hidden.php``
``label``  ``label``          ``FrameworkBundle:Form:label.php``
``render`` ���L�Q��           ���L�Q��
========== ================== ==================

``render`` �w���p�[�́A�����_�����O����e���v���[�g���t�B�[���h�̃N���X�����A���_�[�X�R�A�ŋ�؂������̂����ɂ��đI�ԂƂ��낪�A���Ə����قȂ�܂��B�Ⴆ�΁A ``TextareaField`` �C���X�^���X�������_�����O����ۂɂ́A ``textarea_field`` �u���b�N�܂��� ``textarea_field.php`` �e���v���[�g��T���܂��B

.. configuration-block::

    .. code-block:: html+jinja

        {# TwigBundle::form.html.twig #}

        {% block textarea_field %}
            <textarea {% display field_attributes %}>{{ field.displayedData }}</textarea>
        {% endblock textarea_field %}

    .. code-block:: html+php

        <!-- FrameworkBundle:Form:textarea_field.php -->
        <textarea id="<?php echo $field->getId() ?>" name="<?php echo $field->getName() ?>" <?php if ($field->isDisabled()): ?>disabled="disabled"<?php endif ?>>
            <?php echo $view->escape($field->getDisplayedData()) ?>
        </textarea>

�u���b�N��e���v���[�g�����݂��Ȃ��ꍇ�A���\�b�h�̓t�B�[���h�̌p�����N���X�̃u���b�N��e���v���[�g��T���܂��B�\�����p�����N���X�Ɠ����ɂȂ�悤�A�f�t�H���g�� ``collection_field`` �u���b�N�����݂��Ȃ��̂͂��̂��߂ł��B

�t�B�[���h�̕\�����J�X�^�}�C�Y����
--------------------------------

�t�B�[���h���J�X�^�}�C�Y�����ԊȒP�ȕ��@�́A ``render`` �w���p�[�ւ̈����Ƃ��ăJ�X�^��HTML������n���Ă�邱�Ƃł��B

.. configuration-block::

    .. code-block:: jinja

        {{ form_field(form.title, { 'class': 'important' }) }}

    .. code-block:: html+php

        <?php echo $view['form']->render($form['title'], array(
            'class' => 'important'
        )) ?>

``ChoiceField`` �̂悤�Ȃ������̃t�B�[���h�́A�t�B�[���h�̕\�����J�X�^�}�C�Y���邽�߂̃p�����[�^���󂯎�邱�Ƃ��ł��܂��B�����̃p�����[�^��2�Ԗڈȍ~�̈����Ƃ��ēn���܂��B

.. configuration-block::

    .. code-block:: jinja

        {{ form_field(form.country, {}, { 'separator': ' -- Other countries -- ' }) }}

    .. code-block:: html+php

        <?php echo $view['form']->render($form['country'], array(), array(
            'separator' => ' -- Other countries -- '
        )) ?>

�S�Ẵw���p�[�́A�w���p�[��HTML�o�͂����S�ɕς�����悤�ɁA�Ō�̈����Ƃ��ăe���v���[�g�l�[�����󂯎�邱�Ƃ��ł��܂��B

.. configuration-block::

    .. code-block:: jinja

        {{ form_field(form.title, {}, {}, 'HelloBundle::form.html.twig') }}

    .. code-block:: html+php

        <?php echo $view['form']->render($form['title'], array(), array(), 
            'HelloBundle:Form:text_field.php'
        ) ?>

�t�H�[���̃e�[�~���O (Twig �̂�)
~~~~~~~~~~~~~~~~~~~~~~~~

�Ō�̗�Ƃ��āA ``HelloBundle::form.html.twig`` �Ƃ����A�I�[�o�[���C�h�������t�B�[���h��HTML�\�����`����u���b�N���܂񂾕��ʂ� Twig �e���v���[�g�������܂��B

.. code-block:: html+jinja

    {# HelloBundle/Resources/views/form.html.twig #}

    {% block textarea_field %}
        <div class="textarea_field">
            <textarea {% display field_attributes %}>{{ field.displayedData }}</textarea>
        </div>
    {% endblock textarea_field %}

���̗�ł́A ``textarea_field`` ���Ē�`����Ă��܂��B�f�t�H���g�̕\����ς������ɁATwig �l�C�e�B�u�̌p���@�\���g���ăf�t�H���g�̃u���b�N���g�����邱�Ƃ��ł��܂��B

.. code-block:: html+jinja

    {# HelloBundle/Resources/views/form.html.twig #}

    {% extends 'TwigBundle::form.html.twig' %}

    {% block date_field %}
        <div class="important_date_field">
            {{ parent() }}
        </div>
    {% endblock date_field %}

�^����ꂽ�t�H�[���̑S�Ẵt�B�[���h���J�X�^�}�C�Y���������́A ``form_theme`` �^�O���g���܂��傤�B

.. code-block:: jinja

    {% form_theme form 'HelloBundle::form.html.twig' %}

���̌Ăяo���̌�A ``form`` ��� ``form_field`` �֐����Ăяo�����͏�ɁASymfony2�̓f�t�H���g�̕\���ɖ߂�O�Ƀe���v���[�g���̕\����T���܂��B

�t�B�[���h�u���b�N������̃e���v���[�g���Œ�`����Ă���ꍇ�A�����Â����ꂽ�z��Ƃ��Ēǉ����Ă��������B

.. code-block:: jinja

    {% form_theme form ['HelloBundle::form.html.twig', 'HelloBundle::form.html.twig', 'HelloBundle::hello_form.html.twig'] %}

�t�H�[���S�� (��̂悤��) ���邢�̓t�B�[���h�O���[�v�ɑ΂��ăe�[�}���������܂��B

.. code-block:: jinja

    {% form_theme form.user 'HelloBundle::form.html.twig' %}

�ŏI�I�ɁA�A�v���P�[�V�����̂��ׂẴt�H�[���̕\�����J�X�^�}�C�Y���邱�Ƃ́A�R���t�B�M�����[�V����������\�ł��B

.. configuration-block::

    .. code-block:: yaml

        # app/config/config.yml
        twig:
            form:
                resources: [BlogBundle::form.html.twig, TwigBundle::form.html.twig]

    .. code-block:: xml

        <!-- app/config/config.xml -->
        <twig:config>
            <twig:form>
                <twig:resource>BlogBundle::form.html.twig</twig:resource>
                <twig:resource>TwigBundle::form.html.twig</twig:resource>
            </twig:form>
        </twig:config>

    .. code-block:: php

        // app/config/config.php
        $container->loadFromExtension('twig', array('form' => array(
            'resources' => array('BlogBundle::form.html.twig', 'TwigBundle::form.html.twig),
        )));

.. tip::

    �t�H�[���֐���^�O���e���v���[�g���������Ƃ��Ď��ꍇ�͂��ł��A ``_self`` �����Ɏg�p���邱�Ƃ��ł��܂��B�܂��A���̃e���v���[�g�̒��ŃJ�X�^�}�C�Y�𒼐ڒ�`���邱�Ƃ��\�ł��B

    .. code-block:: jinja

        {% form_theme form _self %}

        {% block textarea_field %}
            ...
        {% endblock %}

        {{ form_field(form.description, {}, {}, _self) }}

����
-----------

�t�H�[���̎�����s�����́A�S�Ẵt�B�[���h���蓮�Ń����_�����O�������ɁA ``render`` �w���p�[���t�H�[����Ŏg�p�ł��܂��B

.. configuration-block::

    .. code-block:: html+jinja

        <form action="#" {{ form_enctype(form) }} method="post">
            {{ form_field(form) }}
            <input type="submit" />
        </form>

    .. code-block:: html+php

        <form action="#" <?php echo $view['form']->enctype($form) ?> method="post">
            <?php echo $view['form']->render($form) ?>

            <input type="submit" />
        </form>

``Form`` �N���X�ɑ΂��ău���b�N��e���v���[�g����`����Ă��Ȃ����Ƃ���A�p�����N���X�̈�ł��� ``FieldGroup`` ������Ɏg�p����܂��B

.. configuration-block::

    .. code-block:: html+jinja

        {# TwigBundle::form.html.twig #}

        {% block field_group %}
            {{ form_errors(field) }}
            {% for child in field %}
                {% if not child.ishidden %}
                    <div>
                        {{ form_label(child) }}
                        {{ form_errors(child) }}
                        {{ form_field(child) }}
                    </div>
                {% endif %}
            {% endfor %}
            {{ form_hidden(field) }}
        {% endblock field_group %}

    .. code-block:: html+php

        <!-- FrameworkBundle:Form:group/table/field_group.php -->

        <?php echo $view['form']->errors($field) ?>

        <div>
            <?php foreach ($field->getVisibleFields() as $child): ?>
                <div>
                    <?php echo $view['form']->label($child) ?>
                    <?php echo $view['form']->errors($child) ?>
                    <?php echo $view['form']->render($child) ?>
                </div>
            <?php endforeach; ?>
        </div>

        <?php echo $view['form']->hidden($field) ?>

.. caution::

    The ``render`` method is not very flexible and should only be used to
    build prototypes.
    ``render`` ���\�b�h�͂���قǏ_�������킯�ł͂Ȃ��̂ŁA�{��̍ۂɂ̂ݎg�p����̂��悢�ł��傤�B
