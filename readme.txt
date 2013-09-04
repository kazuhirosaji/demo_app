http://railstutorial.jp/chapters/a-demo-app.html#top

2�� �f���A�v���̍쐬

2.1 �A�v���̌v��
$ cd rails_projects
$ rails new demo_app
$ cd demo_app
�ɂ�demo�A�v���쐬

Gemfile���X�V���āA�����C���X�g�[��

$ bundle update
$ bundle install --without production


2.2 Users ���\�[�X
Users���\�[�X(�f�[�^���f����Web�C���^�[�t�F�C�X)���A
Rails�v���W�F�N�g�ɕW����������Ă���scaffold�W�F�l���[�^�Ő������܂��B

scaffold�R�}���h�̈����ɂ́A���\�[�X����P���`�ɂ������� (���̏ꍇ��User) ��
�g�p���A�K�v�ɉ����ăf�[�^���f���̑������I�v�V�����Ƃ��ăp�����[�^�ɒǉ����܂�

$ rails generate scaffold User name:string email:string

# id�p�����[�^��Rails�ɂ���Ď����I�Ɏ�L�[�Ƃ���
# �f�[�^�x�[�X�ɒǉ�����邽�߁A�ǉ��s�v


�f�[�^�x�[�X���쐬������ARake�R�}���h��Make���s��

$ bundle exec rake db:migrate

# �f�[�^�x�[�X���X�V���Ausers�f�[�^���f�����쐬����
# ���݂�Gemfile�ɑΉ�����o�[�W������Rake���m���Ɏ��s�����悤�ɂ��邽�߂ɁA
# rake�����s����Ƃ���bundle exec���g�p���Ă���


���[�J��Web�T�[�o���N������
$ rails s

 http://localhost:3000/

http://localhost:3000/users ���Ǝw�肷�邱�ƂŃy�[�W���{���ł���

URI			�A�N�V����	���l
/users		index	���ׂẴ��[�U�[���ꗗ����y�[�W
/users/1	show	id=1�̃��[�U�[��\������y�[�W
/users/new	new		�V�K���[�U�[���쐬����y�[�W
/users/1/edit	edit	id=1�̃��[�U�[��ҏW����y�[�W

2.2.2 MVC�̋���

2.3Mircroposts ���\�[�X
Users�Ɠ��l��Micropost�̃��\�[�X���쐬����

$ rails generate scaffold Micropost content:string user_id:integer

�V�����f�[�^���f���Ńf�[�^�x�[�X���X�V(Make���s��)
$ bundle exec rake db:migrate

$ rails s ��Server�N��

http://localhost:3000/microposts�@�ŉ{���\

micropost.rb(Model)�Ɉȉ��̍s��ǉ����āA
�����������s�����B
#  validates :content, :length => { :maximum => 10 }

2.3.3���[�U�[�ƃ}�C�N���|�X�g��has_many�Ŋ֘A�Â���

