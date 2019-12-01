#3. You are going to create your first Dockerfile to containerize Rails applications. That’s
#a special configuration: this particular Dockerfile will be generic, and called in another Dockerfile

FROM ft-rails:on-build

LABEL maintainer="lrorscha@student.21-school.ru"

EXPOSE 3000
CMD ["rails", "s", "-b", "0.0.0.0", "-p", "3000"]

#docker run --name rails -p 3000:3000 -d rails
