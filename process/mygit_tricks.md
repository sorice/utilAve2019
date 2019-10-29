Not commit your password, secret key and others

passwd = os.enviroment['PASSWORD']

secret_key = os.enviroment.get('SECRET_KEY')

database_url = os.enviroment.get('DATABASE_URL','sqlite:///')

#Tag and comment the actual last commit
git tag -a v0.1 -m "After first Google Cloud Service study"

git clone -b 'v1.9.5' --single-branch https://github.com/git/git.git git-1.9.5
The benefit: Git will receive objects and (need to) resolve deltas for the specified branch/tag only - while checking out the exact same amount of files! Depending on the source repository, this will save you a lot of disk space. (Plus, it'll be much quicker.)


