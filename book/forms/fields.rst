�t�H�[���t�B�[���h
===========

�t�H�[����1���邢�͕����̃t�H�[���t�B�[���h����Ȃ��Ă��܂��B���ꂼ��̃t�B�[���h�� :class:`Symfony\\Component\\Form\\FormFieldInterface` �����������N���X�̃I�u�W�F�N�g�ł��B�t�B�[���h�͕W�������ꂽ�\���Ɛl�Ԃ̓ǂ߂�\���̊ԂŁA�f�[�^��ϊ����܂��B

 ``DateField`` ���Ɍ��Ă݂܂��傤�B���Ȃ��̃A�v���P�[�V���������t�𕶎��񂠂邢�� ``DateTime`` �I�u�W�F�N�g�Ƃ��ĕۑ��������ŁA���[�U�̓h���b�v�_�E���œ��t��I���������Ƃ��܂��B ``DateField`` �̓����_�����O�ƌ^�ϊ���S�����܂��B

�R�A�t�B�[���h�I�v�V����
------------------

�S�Ẵr���g�C�����ꂽ�t�B�[���h�́A���ꂼ��̃R���X�g���N�^���ŃI�v�V�����̔z����󂯎�邱�Ƃ��ł��܂��B�֋X��A�����̃R�A�t�B�[���h�͂������̃I�v�V���������O�ɒ�`���ꂽ :class:`Symfony\\Component\\Form\\Field` �̃T�u�N���X�ɂȂ��Ă��܂��B

``data``
~~~~~~~~

�t�H�[�����쐬����ہA���ꂼ��̃t�B�[���h�͍ŏ��A�t�H�[���̃h���C���I�u�W�F�N�g�̑Ή�����v���p�e�B�̒l��\�����܂��B�����̏����l���㏑���������ꍇ�A ``data`` �I�v�V�����Őݒ肪�ł��܂��B

.. code-block:: php

    use Symfony\Component\Form\HiddenField
    
    $field = new HiddenField('token', array(
        'data' => 'abcdef',
    ));
    
    assert('abcdef' === $field->getData());

.. note::

     ``data`` �I�v�V�������g�p�������A�t�B�[���h�̓h���C���I�u�W�F�N�g�ɂ͏������݂��s���܂���B����́A ``property_path`` �I�v�V�������ÖٓI�� ``null`` �ɂȂ邽�߂ł��B�ڂ����� :ref:`form-field-property_path` ���Q�Ƃ��Ă��������B

``required``
~~~~~~~~~~~~

�f�t�H���g�ł́A���ꂼ��� ``Field`` �͒l���K�{�ł��邱�Ƃ��O��ƂȂ��Ă��܂��B���̂��߁A��̒l�͑��M����܂���B���̐ݒ�͓���Ƃ������̃t�B�[���h�̃����_�����O�ɉe����^���܂��B�Ⴆ�� ``ChoiceField`` �́A�K�{�łȂ���΋�̑I�������܂݂܂��B

.. code-block:: php

    use Symfony\Component\Form\ChoiceField
    
    $field = new ChoiceField('status', array(
        'choices' => array('tbd' => 'To be done', 'rdy' => 'Ready'),
        'required' => false,
    ));

``disabled``
~~~~~~~~~~~~

���[�U�Ƀt�B�[���h�̒l��ύX���������Ȃ��ꍇ�A ``disabled`` �I�v�V������ ``true`` �ɐݒ肷�邱�Ƃ��ł��܂��B�����鑗�M�f�[�^�͖�������܂��B

.. code-block:: php

    use Symfony\Component\Form\TextField
    
    $field = new TextField('status', array(
        'data' => 'Old data',
        'disabled' => true,
    ));
    $field->submit('New data');
    
    assert('Old data' === $field->getData());

``trim``
~~~~~~~~

���̓t�B�[���h�̐擪�▖���ɃX�y�[�X�������������Ă��܂����[�U���������񂢂܂��B�t�H�[���̃t���[�����[�N�͂����̃X�y�[�X�������I�ɍ폜���܂��B�����X�y�[�X�����̂܂܂ɂ������̂Ȃ�A ``trim`` �I�v�V������ ``false`` �ɐݒ肵�Ă��������B

.. code-block:: php

    use Symfony\Component\Form\TextField
    
    $field = new TextField('status', array(
        'trim' => false,
    ));
    $field->submit('   Data   ');
    
    assert('   Data   ' === $field->getData());

.. _form-field-property_path:

``property_path``
~~~~~~~~~~~~~~~~~

�t�B�[���h�́A�f�t�H���g�Ńt�H�[���̃h���C���I�u�W�F�N�g�̃v���p�e�B�l��\�����܂��B�t�H�[�������M���ꂽ���A���M���ꂽ�l�̓I�u�W�F�N�g�ɏ����߂���܂��B

�t�B�[���h����ǂݏo���ꂽ�A���邢�̓t�B�[���h�֏������񂾃v���p�e�B���㏑���������ꍇ�ɂ́A ``property_path`` �I�v�V������ݒ�ł��܂��B���̃I�v�V�����̃f�t�H���g�l�̓t�B�[���h�̖��O�ɂȂ��Ă��܂��B

.. code-block:: php

    use Symfony\Component\Form\Form
    use Symfony\Component\Form\TextField
    
    $author = new Author();
    $author->setFirstName('Your name...');
    
    $form = new Form('author');
    $form->add(new TextField('name', array(
        'property_path' => 'firstName',
    )));
    $form->bind($request, $author);
    
    assert('Your name...' === $form['name']->getData());

�v���p�e�B�p�X�̂��߂ɁA�h���C���I�u�W�F�N�g�̃N���X�Ɉȉ��̂����ꂩ���K�v�ł��B

1. ��v����p�u���b�N�ȃv���p�e�B�A�܂���
2. "set"�܂���"get"����n�܂�A�v���p�e�B�p�X�������A�p�u���b�N�ȃZ�b�^����уQ�b�^

�v���p�e�B�p�X�́A�h�b�g(.)���g�����Ƃœ���q�ɂȂ����I�u�W�F�N�g���Q�Ƃł��܂��B

.. code-block:: php

    use Symfony\Component\Form\Form
    use Symfony\Component\Form\TextField
    
    $author = new Author();
    $author->getEmail()->setAddress('me@example.com');
    
    $form = new Form('author');
    $form->add(new EmailField('email', array(
        'property_path' => 'email.address',
    )));
    $form->bind($request, $author);
    
    assert('me@example.com' === $form['email']->getData());

�p����[]���g���āA����q�ɂȂ����z��̃G���g���� ``\Traversable`` �����������I�u�W�F�N�g���Q�Ƃł��܂��B

.. code-block:: php

    use Symfony\Component\Form\Form
    use Symfony\Component\Form\TextField
    
    $author = new Author();
    $author->setEmails(array(0 => 'me@example.com'));
    
    $form = new Form('author');
    $form->add(new EmailField('email', array(
        'property_path' => 'emails[0]',
    )));
    $form->bind($request, $author);
    
    assert('me@example.com' === $form['email']->getData());

�v���p�e�B�p�X�� ``null`` �̏ꍇ�A�t�B�[���h�ɂ̓h���C���I�u�W�F�N�g����̓ǂݏ����͂ł��܂���B����́A�Œ�l�����t�B�[���h���~�����ꍇ�ɖ��ɗ����܂��B

.. code-block:: php

    use Symfony\Component\Form\HiddenField
    
    $field = new HiddenField('token', array(
        'data' => 'abcdef',
        'property_path' => null,
    ));
    
``data`` �I�v�V������ݒ肵���ꍇ�A``property_path`` �͏�� ``null`` �ɂȂ�̂���ʓI�ł��B�]���āA�O�̃R�[�h��͈ȉ��̂悤�ɒP���ɂł��܂��B

.. code-block:: php

    use Symfony\Component\Form\HiddenField
    
    $field = new HiddenField('token', array(
        'data' => 'abcdef',
    ));

.. note::

    �J�X�^���̃f�t�H���g�l��ݒ肵��������ǂ��̂܂܃h���C���I�u�W�F�N�g�ɏ������݂����ꍇ�́A ``property_path`` ���蓮�œn���K�v������܂��B

    .. code-block:: php

        use Symfony\Component\Form\TextField
        
        $field = new TextField('name', array(
            'data' => 'Custom default...',
            'property_path' => 'token',
        ));
    
    Usually this is not necessary, because you should rather the default value
    of the ``token`` property in your domain object.
    �{���̓h���C���I�u�W�F�N�g���� ``token`` �v���p�e�B�̃f�t�H���g�l�����߂�ׂ��Ȃ̂ŁA�ʏ�͂������������Ƃ͕K�v�ɂȂ�܂���B

�r���g�C���t�B�[���h
---------------

Symfony2�͈ȉ��̃t�B�[���h������Ă��܂��B

.. toctree::
    :hidden:

    fields/index

.. include:: fields/map.rst.inc

