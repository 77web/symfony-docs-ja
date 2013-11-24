.. index::
    single: Forms; Fields; currency

.. note::

   * �Ώۃo�[�W�����F2.3
   * �|��X�V���F2013/11/24


currency �t�B�[���h�^�C�v
===================

``currency`` �^�C�v��:doc:`choice �^�C�v </reference/forms/types/choice>`�̃T�u�Z�b�g�ŁA
���[�U�[��`3-letter ISO 4217`_ �̑�ʂ̒ʉ݃��X�g����I�����邱�Ƃ��ł��܂��B

``choice``�^�C�v�Ƃ͈قȂ�A``choices``�܂���``choice_list``�I�v�V��������肷��K�v�͂Ȃ��A
�t�B�[���h�^�C�v�Ƃ��Ď����I�ɑ�ʂ̒ʉ݃��X�g���g���܂��B�����̃I�v�V�����̂ǂ��炩���蓮�Őݒ肷��
���Ƃ�*�o���܂�*���A���̏ꍇ��``choice``�^�C�v�𒼐ڎg���ׂ��ł��B

+-------------+------------------------------------------------------------------------+
| �Ή�����^�O| �����̃^�O�ŗ��p�ł��܂� (see :ref:`forms-reference-choice-tags`)      |
+-------------+------------------------------------------------------------------------+
| �㏑�����ꂽ| - `choices`_                                                           |
| �I�v�V����  |                                                                        |
+-------------+------------------------------------------------------------------------+
| �p�����ꂽ  | - `multiple`_                                                          |
| �I�v�V����  | - `expanded`_                                                          |
|             | - `preferred_choices`_                                                 |
|             | - `empty_value`_                                                       |
|             | - `error_bubbling`_                                                    |
|             | - `required`_                                                          |
|             | - `label`_                                                             |
|             | - `read_only`_                                                         |
|             | - `disabled`_                                                          |
|             | - `mapped`_                                                            |
+-------------+------------------------------------------------------------------------+
| �e�@�^�C�v  | :doc:`choice </reference/forms/types/choice>`                          |
+-------------+------------------------------------------------------------------------+
| �N���X      | :class:`Symfony\\Component\\Form\\Extension\\Core\\Type\\CurrencyType` |
+-------------+------------------------------------------------------------------------+

�㏑�����ꂽ�I�v�V����
------------------

choices
~~~~~~~

**�f�t�H���g**: ``Symfony\Component\Intl\Intl::getCurrencyBundle()->getCurrencyNames()``

choisces�I�v�V�����̓f�t�H���g�ł��ׂĂ̒ʉ݂ɂȂ�܂��B

�p�����ꂽ�I�v�V����
-----------------

�ȉ��̃I�v�V������ :doc:`choice</reference/forms/types/choice>` �^�C�v���p�����Ă��܂�:

.. include:: /reference/forms/types/options/multiple.rst.inc

.. include:: /reference/forms/types/options/expanded.rst.inc

.. include:: /reference/forms/types/options/preferred_choices.rst.inc

.. include:: /reference/forms/types/options/empty_value.rst.inc

.. include:: /reference/forms/types/options/error_bubbling.rst.inc

�ȉ��̃I�v�V������ :doc:`date</reference/forms/types/form>` �^�C�v���p�����Ă��܂�:

.. include:: /reference/forms/types/options/required.rst.inc

.. include:: /reference/forms/types/options/label.rst.inc

.. include:: /reference/forms/types/options/read_only.rst.inc

.. include:: /reference/forms/types/options/disabled.rst.inc

.. include:: /reference/forms/types/options/mapped.rst.inc

.. _`3-letter ISO 4217`: http://ja.wikipedia.org/wiki/ISO_4217

.. 2013/11/24 yositani2002 3842f599eb277e387c820816c91a099d6be50df2
