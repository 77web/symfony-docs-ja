.. index::
   single: Forms

�t�H�[��������
==================

Symfony2�̓r���g�C�����ꂽ�t�H�[���R���|�[�l���g������Ă��܂��B����ɂ��AHTML�t�H�[����\��������A�����_�����O������A���M�����肷�邱�Ƃ��ł��܂��B

Symfony2�� :class:`Symfony\\Component\\HttpFoundation\\Request` �N���X�P�Ƃő��M�����t�H�[�����������邱�Ƃ��\�Ȃ����łȂ��A�t�H�[���R���|�[�l���g�͈ȉ��̂悤�ȃt�H�[���Ɋ֘A�������X�̈�ʓI�����̖ʓ|�����邱�Ƃ��ł��܂��B

1. �����������ꂽ�t�H�[���t�B�[���h���܂�HTML�t�H�[���̕\��
2. ���M���ꂽ�f�[�^��PHP�f�[�^�^�ւ̕ϊ�
3. POPOs (Plain Old PHP Objects)����̃f�[�^�̓ǂݍ��݁A���邢��POPOs�ւ̃f�[�^�̏�������
4. Symfony2�� ``Validator`` ���g�p�����A���M���ꂽ�f�[�^�̃o���f�[�V����
5. �f�[�^���M��CSRF�U������̕ی�

�T�v
--------

�R���|�[�l���g�͈ȉ��̃R���Z�v�g����Ȃ��Ă��܂��B

*�t�B�[���h*
  ���M�f�[�^��W�������ꂽ�l�ɕϊ�����N���X�ł��B

*�t�H�[��*
  �o���f�[�V�������ǂ̂悤�ɍs���̂���`���ꂽ�t�B�[���h�̏W�܂�ł��B

*�e���v���[�g*
  HTML�Ƀt�H�[����t�B�[���h�������_�����O����t�@�C���ł��B

*�h���C���I�u�W�F�N�g*
  �f�t�H���g�l��ǂ��ɑ��M�f�[�^���������܂ꂽ�����t�H�[��������邽�߂̃I�u�W�F�N�g�ł��B

�t�H�[���R���|�[�l���g�̓��삪�ˑ����Ă���̂́AHttpFoundation��Validator�R���|�[�l���g�����ł��B���ۉ��̋@�\���g�p���������ɂ́APHP�̍��ۉ��g�����K�v�ɂȂ�܂��B

�t�H�[���I�u�W�F�N�g
------------

�t�H�[���I�u�W�F�N�g�́A���M�f�[�^�����Ȃ��̃A�v���P�[�V�����Ŏg���Ă���t�H�[�}�b�g�ɕϊ�����t�B�[���h�̏W�܂���J�v�Z�������܂��B�t�H�[���N���X�� :class:`Symfony\\Component\\Form\\Form` �̃T�u�N���X�Ƃ��Đ�������܂��B��A�̃t�B�[���h�����t�H�[��������������ɂ́A``configure()`` ���\�b�h���g�p���Ă��������B

.. code-block:: php

    // src/Sensio/HelloBundle/Contact/ContactForm.php
    namespace Sensio\HelloBundle\Contact;

    use Symfony\Component\Form\Form;
    use Symfony\Component\Form\TextField;
    use Symfony\Component\Form\TextareaField;
    use Symfony\Component\Form\CheckboxField;
    
    class ContactForm extends Form
    {
        protected function configure()
        {
            $this->add(new TextField('subject', array(
                'max_length' => 100,
            )));
            $this->add(new TextareaField('message'));
            $this->add(new TextField('sender'));
            $this->add(new CheckboxField('ccmyself', array(
                'required' => false,
            )));
        }
    }

�t�H�[���� ``Field`` �I�u�W�F�N�g����Ȃ��Ă��܂��B���̗�̏ꍇ�A�t�H�[���� ``subject``�A ``message``�A ``sender``�A ``ccmyself`` �̊e�t�B�[���h����Ȃ��Ă��܂��B ``TextField``�A�@``TextareaField``�A ``CheckboxField`` �́A�g�p�\�ȃt�H�[���t�B�[���h�̂�����3�ł��B�g�p�\�ȃt�H�[���t�B�[���h�̑S���X�g�́A :doc:`Form fields <fields>` �ɂ���܂��B

�R���g���[�����Ńt�H�[�����g�p����
----------------------------

�R���g���[�����Ńt�H�[�����g�p����ۂ̈�ʓI�ȃp�^�[���́A�ȉ��̂悤�ɂȂ�܂��B

.. code-block:: php

    // src/Sensio/HelloBundle/Controller/HelloController.php
    public function contactAction()
    {
        $contactRequest = new ContactRequest($this->get('mailer'));
        $form = ContactForm::create($this->get('form.context'), 'contact');
        
        // POST���N�G�X�g�����M���ꂽ��A���M�f�[�^��$contactRequest�ɓ���A
        // �I�u�W�F�N�g�̃o���f�[�V�������s��
        $form->bind($this->get('request'), $contactRequest);
        
        // �t�H�[�������M����A���e���L���ȏꍇ��...
        if ($form->isValid()) {
            $contactRequest->send();
        }

        // $contactRequest���̒l�Ƌ��Ƀt�H�[����\��
        return $this->render('HelloBundle:Hello:contact.html.twig', array(
            'form' => $form
        ));
    }
   
���̗�ɂ�2�̃R�[�h�p�X������܂��B

1. �t�H�[�������M����Ȃ����L���łȂ������ꍇ�A�P���Ƀe���v���[�g�Ɉړ����܂��B
2. �t�H�[�������M����L���������ꍇ�A�R���^�N�g���N�G�X�g�����M����܂��B

���̗�ł́A ``create()`` static���\�b�h�Ńt�H�[�����쐬���Ă��܂��B���̃��\�b�h�́A�f�t�H���g�T�[�r�X(�Ⴆ�� ``Validator``)�ƁA�t�H�[�������삷�邽�߂ɕK�v�Ȑݒ�̑S�Ă��܂ރt�H�[���R���e�L�X�g��K�v�Ƃ��܂��B

.. note:

    ����Symfony2���̂��邢��Symfony2�̃T�[�r�X�R���e�i���g�p���Ȃ��ꍇ�ł��S�z����܂���B``FormContext`` �� ``Request`` �͊ȒP�Ɏ蓮�ō쐬�ł��܂��B
    
    .. code-block:: php
    
        use Symfony\Component\Form\FormContext;
        use Symfony\Component\HttpFoundation\Request;
        
        $context = FormContext::buildDefault();
        $request = Request::createFromGlobals();

�t�H�[���ƃh���C���I�u�W�F�N�g
------------------------

�O�̗�ł́A ``ContactRequest`` �̓t�H�[���Ɋ֘A�Â��Ă��܂����B���̃I�u�W�F�N�g�̃v���p�e�B�l�́A�t�H�[���t�B�[���h�𖄂߂�̂Ɏg���܂��B�o�C���h�̌�A���M�f�[�^�̒l�̓I�u�W�F�N�g�ɍēx�������܂�܂��B ``ContactRequest`` �N���X�͈ȉ��̂悤�ɂȂ��Ă��܂��B

.. code-block:: php

    // src/Sensio/HelloBundle/Contact/ContactRequest.php
    namespace Sensio\HelloBundle\Contact;

    class ContactRequest
    {
        protected $subject = 'Subject...';
        
        protected $message;
        
        protected $sender;
        
        protected $ccmyself = false;
        
        protected $mailer;
        
        public function __construct(\Swift_Mailer $mailer)
        {
            $this->mailer = $mailer;
        }
        
        public function setSubject($subject)
        {
            $this->subject = $subject;
        }
        
        public function getSubject()
        {
            return $this->subject;
        }
        
        // ���̃v���p�e�B�p�̃Z�b�^�ƃQ�b�^
        // ...
        
        public function send()
        {
            // ���[���𑗐M
            $message = \Swift_Message::newInstance()
                ->setSubject($this->subject)
                ->setFrom($this->sender)
                ->setTo('me@example.com')
                ->setBody($this->message);
                
            $this->mailer->send($message);
        }
    }
    
.. note::

    ���[�����M�ɂ��Ă̏ڍׂ� :doc:`Emails </cookbook/email>` ���Q�Ƃ��Ă��������B

�t�H�[�����̊e�t�B�[���h�ɑ΂��āA�h���C���I�u�W�F�N�g�̃N���X�Ɉȉ��̂����ꂩ���K�v�ł��B

1. �t�B�[���h�����܂ރp�u���b�N�ȃv���p�e�B�A�܂���
2. "set"�܂���"get"����n�܂�A�擪���啶���̃t�B�[���h���������A�p�u���b�N�ȃZ�b�^����уQ�b�^
   
���M�f�[�^�̃o���f�[�V����
-------------------------

�t�H�[���́A���M���ꂽ�t�H�[���̒l���L���ł��邩���m�F���邽�߁A ``Validator`` �R���|�[�l���g���g�p���܂��B�h���C���I�u�W�F�N�g��A�t�H�[����A���邢�̓t�B�[���h��̑S�Ă̐���́A ``bind()`` ���Ăяo���ꂽ���Ƀo���f�[�V���������s����܂��B�s���ȃf�[�^���������t�H�[���𑗐M�ł��Ȃ����Ƃ��m���ɂ��邽�߂ɁA ``ContactRequest`` �ɂ͂������̐��񂪒ǉ�����܂��B

.. code-block:: php

    // src/Sensio/HelloBundle/Contact/ContactRequest.php
    namespace Sensio\HelloBundle\Contact;

    class ContactRequest
    {
        /**
         * @validation:MaxLength(100)
         * @validation:NotBlank
         */
        protected $subject = 'Subject...';
        
        /**
         * @validation:NotBlank
         */
        protected $message;
        
        /**
         * @validation:Email
         * @validation:NotBlank
         */
        protected $sender;
        
        /**
         * @validation:AssertType("boolean")
         */
        protected $ccmyself = false;
        
        // �R�[�h������...
    }

����𖞂����Ȃ��ꍇ�A�Ή�����t�H�[���t�B�[���h�̉��ɃG���[���\������܂��B�ڂ����́A :doc:`�o���f�[�V�����̐��� </book/validator/constraints>` ���Q�Ƃ��Ă��������B

�t�H�[���t�B�[���h��������������
----------------------------------

Doctrine2�܂���Symfony�� ``Validator`` ���g�p���Ă���̂ł���΁ASymfony�͂��Ȃ��̃h���C���N���X�ɂ��Ċ��ɂ��Ȃ�̂��Ƃ�m���Ă��邱�ƂɂȂ�܂��B�ǂ̃f�[�^�^�C�v���v���p�e�B���f�[�^�x�[�X���ŉi�������邽�߂Ɏg���邩�A�v���p�e�B���ǂ�ȃo���f�[�V�����̐���������Ă��邩�A�Ƃ��������Ƃł��B�t�H�[���R���|�[�l���g�́A�ǂ�Ȑݒ�łǂ̃t�B�[���h�^�C�v�������ׂ������u�����v���邽�߂ɁA�����̏����g�����Ƃ��ł��܂��B

���̋@�\���g�p����ɂ́A�֘A����h���C���I�u�W�F�N�g�̃N���X���t�H�[�����m���Ă���K�v������܂��B���̂悤�ȃN���X�́A ``setDataClass()`` ���g�p���A�N���X���̊��S�C�����𕶎���Ƃ��ēn�����Ƃɂ���āA�t�H�[���� ``configure()`` ���\�b�h�̒��Őݒ肷�邱�Ƃ��ł��܂��B�v���p�e�B�������� ``add()`` ���Ăяo���ƁA�œK�ȃt�B�[���h�������I�ɍ쐬����܂��B

.. code-block:: php

    // src/Sensio/HelloBundle/Contact/ContactForm.php
    class ContactForm extends Form
    {
        protected function configure()
        {
            $this->setDataClass('Sensio\\HelloBundle\\Contact\\ContactRequest');
            $this->add('subject');  // max_length��100������TextField
                                    // (@MaxLength����ɂ��)
            $this->add('message');  // TextField
            $this->add('sender');   // EmailField (@Email����ɂ��)
            $this->add('ccmyself'); // CheckboxField
                                    // (@AssertType("boolean")����ɂ��)
        }
    }

�����t�B�[���h�̐����́A������񂢂ł��������Ƃ͌���܂���B ``message`` �Ƃ����v���p�e�B�ɑ΂���Symfony�� ``TextField`` ��������Ƃ��āA�o���f�[�V�����̐��񂩂�͂��Ȃ������� ``TextareaField`` ���~���������Ƃ������Ƃ͕�����Ȃ��̂ł��B�]���āA���̃t�B�[���h�͎蓮�ō쐬���Ȃ��Ă͂Ȃ�܂���B���邢�́A2�ڂ̃p�����[�^��n���āA�t�B�[���h�����̃I�v�V�����𒲐����邱�Ƃ��ł��܂��B�����𐧌����邽�߂ɁA ``max_length`` �I�v�V������ ``sender`` �t�B�[���h�ɒǉ��ł��܂��B

.. code-block:: php

    // src/Sensio/HelloBundle/Contact/ContactForm.php
    class ContactForm extends Form
    {
        protected function configure()
        {
            $this->setDataClass('Sensio\\HelloBundle\\Contact\\ContactRequest');
            $this->add('subject'); 
            $this->add(new TextareaField('message'));
            $this->add('sender', array('max_length' => 50));
            $this->add('ccmyself');
        }
    }
    
�t�H�[���t�B�[���h�̎��������́A�J�����x���グ�A�R�[�h�̏d�������炷�̂ɖ𗧂��܂��B�N���X�v���p�e�B�Ɋւ��������x�ۑ����Ă��܂��΁A���Ƃ�Symfony2�ɑ��̎d����C���邱�Ƃ��ł��܂��B

HTML�Ƃ��ăt�H�[���������_�����O����
-----------------------

In the controller we passed the form to the template in the ``form`` variable.
In the template we can use the ``form_field`` helper to output a raw prototype
of the form.
�R���g���[�����̏ꍇ�A ``form`` �ϐ��Ƀt�H�[�������ăe���v���[�g�ɓn���܂����B�e���v���[�g���̏ꍇ�́A�t�H�[���̐��̃v���g�^�C�v���o�͂��邽�߁A ``form_field`` �w���p�[���g�p�ł��܂��B

.. code-block:: html+jinja

    # src/Sensio/HelloBundle/Resources/views/Hello/contact.html.twig
    {% extends 'HelloBundle::layout.html.twig' %}

    {% block content %}
    <form action="#" method="post">
        {{ form_field(form) }}
        
        <input type="submit" value="Send!" />
    </form>
    {% endblock %}
    
HTML�o�͂��J�X�^�}�C�Y����
---------------------------

In most applications you will want to customize the HTML of the form. You
can do so by using the other built-in form rendering helpers.
�قƂ�ǂ̃A�v���P�[�V�����ɂ����āA�t�H�[����HTML���J�X�^�}�C�Y�������Ȃ邱�Ƃł��傤�B����́A�ʂ̃r���g�C���t�H�[�������_�����O�w���p�[���g�p���邱�Ƃɂ���ĉ\�ɂȂ�܂��B

.. code-block:: html+jinja

    # src/Sensio/HelloBundle/Resources/views/Hello/contact.html.twig
    {% extends 'HelloBundle::layout.html.twig' %}

    {% block content %}
    <form action="#" method="post" {{ form_enctype(form) }}>
        {{ form_errors(form) }}
        
        {% for field in form %}
            {% if not field.ishidden %}
            <div>
                {{ form_errors(field) }}
                {{ form_label(field) }}
                {{ form_field(field) }}
            </div>
            {% endif %}
        {% endfor %}

        {{ form_hidden(form) }}
        <input type="submit" />
    </form>
    {% endblock %}
    
Symfony2�ɂ͈ȉ��̃w���p�[���p�ӂ���Ă��܂��B

*``form_enctype``*
  �t�H�[���^�O�� ``enctype`` �������o�͂��܂��B�t�@�C���̃A�b�v���[�h�̂��߂ɕK�{�ł��B

*``form_errors``*
  �t�B�[���h�܂��̓t�H�[���̃G���[�Ƌ��� ``<ul>`` �^�O���o�͂��܂��B

*``form_label``*
  Outputs the ``<label>`` tag of a field.
  �t�B�[���h�� ``<label>`` �^�O���o�͂��܂��B

*``form_field``*
  �t�B�[���h�܂��̓t�H�[����HTML���o�͂��܂��B

*``form_hidden``*
  �t�H�[���̉B���t�B�[���h���o�͂��܂��B

�t�H�[���̃����_�����O�Ɋւ���ڍׂ� :doc:`�e���v���[�g���Ńt�H�[�����g�p���� <view>` ���Q�Ƃ��Ă��������B

���߂łƂ��������܂��I Symfony2���g���āA�ŏ��̑S�@�\�Ńt�H�[�����쐬�ł��܂����ˁB
