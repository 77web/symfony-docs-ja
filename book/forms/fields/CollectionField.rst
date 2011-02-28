CollectionField
===============

``CollectionField`` �́A�z��� ``Traversable`` �C���^�t�F�[�X�����������I�u�W�F�N�g�𑀍삷�邽�߂̓��ʂȃt�B�[���h�O���[�v�ł��B���̃f�������{���邽�߂ɁA3��E���[���A�h���X��ۑ��ł���悤 ``Customer`` �N���X���g�����܂����B

    class Customer
    {
        // other properties ...

        public $emails = array('', '', '');
    }

�����ŃA�h���X�𑀍�ł���悤�� ``CollectionField`` �������܂��B

    use Symfony\Component\Form\CollectionField;

    $form->add(new CollectionField('emails', array(
        'prototype' => new EmailField(),
    )));

If you set the option "modifiable" to ``true``, you can even add or remove
rows in the collection via JavaScript! The ``CollectionField`` will notice it
and resize the underlying array accordingly.
 "modifiable" �I�v�V������ ``true`` �ɐݒ肷��ꍇ�AJavaScript ���g���ăR���N�V�����ɍs��ǉ�������폜���邱�Ƃ��ł��܂��I ``CollectionField`` �������m�点�Ă���āA��{�ƂȂ�z���K�؂Ƀ��T�C�Y���Ă����ł��傤�B
