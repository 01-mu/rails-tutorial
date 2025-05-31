# Use official Ruby image as a parent image
FROM ruby:3.2-slim

# Install dependencies
RUN apt-get update -qq && \
    apt-get install -y build-essential libsqlite3-dev nodejs npm curl

# Install Yarn
RUN npm install --global yarn

# Set working directory
WORKDIR /myapp

# Install Rails 7.0
RUN gem install rails -v 7.0.0

# Copy Gemfile and Gemfile.lock if they exist (for caching)
COPY Gemfile Gemfile.lock ./

# Install gems (if Gemfile exists)
RUN if [ -f Gemfile ]; then bundle install; fi

# Copy the rest of the app
COPY . .

# Expose port 3000
EXPOSE 3000

# Default command
CMD ["bash", "-c", "bundle install && rails server -b 0.0.0.0"]
