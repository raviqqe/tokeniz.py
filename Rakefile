VENV_DIR = '.venv'


def vsh *args
  sh ". #{VENV_DIR}/bin/activate && #{args.join ' '}"
end


task :test => :clean do
  sh "python3 -m venv #{VENV_DIR}"
  vsh 'pip install mecab-python3'
  vsh 'python setup.py install'
  vsh 'python3 -m nltk.downloader punkt'
  vsh 'nltokeniz data/foo.en'
  vsh 'nltokeniz -l en data/foo.en'
  vsh 'nltokeniz -l ja data/foo.ja'
  vsh 'nltokeniz data/foo.what'
end


task :upload => :test do
    sh 'python3 setup.py sdist bdist_wheel'
    sh 'twine upload dist/*'
end


task :clean do
  sh 'git clean -dfx'
end
